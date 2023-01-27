<?php
/********************************************************************************************************
Revision History:
5/4/2017 12:09 PM
- Added Jameer in the privilege to view Quality Authorization		
9/26/2016 11:15 AM
- Move the menu for Student Pilot Authorization List on lines 3118-3130 because at first it is inside Request folder. It became submenu.
- Added  closing '>' fo <a> on line 2463 for theh folder doesn't show because of it.
9/25/2016 2:54 PM
- Added menu for Student Pilot Authorization List on lines 1993-2003 for IT staffs and lines 2727-2739 for CGI CFI and HOT.
9/21/2016 4:05 PM
- Added menu for Certificate Template on lines 1979-1989 for IT Staffs and lines 3082-3097 for Capt. Jose
9/20/2016 2:51 PM
- Added menu for Quality Authorization on lines 1948-1959 for IT Staffs and lines 4224-4238 for safety account of Elias
ind
9/4/2016 8:30 AM
- Added menu for terms and conditions viewable by IT and HR only(Sehaam) on line 1910-1917
8/24/2016 11:35 AM
- Moved submenus of student attendance before employee attendance.
8/02/2016 9:56 AM
- Modify condition for the login pop ups at line 220. Add && $dept != "1" . To disable it for students.
7/20/2016 4:27 PM
- Added menu for online users viewable by IT only on line 1905-1919
7/20/2016 5:25 PM
- Added lines 218-230 to check if there is current open session for the username
5/9/2016 12:32 PM  - line 381 Added flight_course_flow_report link
3/28/2016 3:08 PM
- Added menu for contact directory viewable by IT and HR only(Sehaam) on line 1783-1796
*********************************************************************************************************/
session_start();
$mydate	= date("Y-m-d");
$comp_name = $_SESSION['comp_name'];
$questionid = $_SESSION['questionid'];
$addinguser = $_SESSION['addinguser'];
$internal =	$_SESSION['internal'];
$external =	$_SESSION['external'];
$checkndex = $_SESSION['checkndex']; 
$leave_request = $_SESSION['leave_request']; 
$stageandchapter = $_SESSION['stageandchapter'];
$chiefins = $_SESSION['chiefins'];
$qam = $_SESSION['qam'];
$sfo = $_SESSION['sfo'];
$hot = $_SESSION['hot'];
$lead_auditor_session = $_SESSION['lead_auditor_session'];
$auditees_session = $_SESSION['auditees_session'];
$groundins = $_SESSION['groundins'];
$flightins = $_SESSION['flightins'];
include "dblinklocal.php";
include "encrypt2.php";
include "address.php";
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<link rel="stylesheet" href="style_new.css" type="text/css" />
<script type="text/javascript" src="scripts/prototype.js"></script>
<script type="text/javascript" src="scripts/lightboxonload.js"></script>
<link rel="stylesheet" href="lightbox.css" media="screen,projection" type="text/css" />
<link rel="shortcut icon" href="image/FUJAA_Logo.png">
<title>Fujaa Software</title>
<script>
function showprocurement()
{document.getElementById('divprocurement').style.display = 'block';}
function show_gs_report()
{document.getElementById('div_gs_report').style.display = 'block';}
function show_gs_tki_report()
{document.getElementById('div_gs_tki_report').style.display = 'block';}
function showstudmenu()
{document.getElementById('divstudmenu').style.display = 'block';}
function showinsmenu()
{document.getElementById('divinsmenu').style.display = 'block';}
function showotherusers()
{document.getElementById('divotherusers').style.display = 'block';}		
function showotherhremp()
{document.getElementById('divotherhremp').style.display = 'block';}		
function showexam()
{document.getElementById('divexam').style.display = 'block';}
function showsms()
{document.getElementById('divsms').style.display = 'block';}				
function showquestion()
{document.getElementById('divquestion').style.display = 'block';}
function showcourse() 
{document.getElementById('divcourse').style.display = 'block';} 
function showacmenu()
{document.getElementById('divacmenu').style.display = 'block';}
function showadminattendance()
{document.getElementById('divadminattendance').style.display = 'block';} 
function showadminattendance_safety()
{document.getElementById('divadminattendance_safety').style.display = 'block';} 								
function showdaily()
{document.getElementById('divdaily').style.display = 'block';}
function showadmindaily()
{document.getElementById('divdailymenu').style.display = 'block';}
function showrequest()
{document.getElementById('divrequestform').style.display = 'block';}
function showattendance()
{document.getElementById('divattendance').style.display = 'block';}
function showrequest2()
{document.getElementById('divrequestform2').style.display = 'block';}	
function showinsdutytime()
{document.getElementById('divinsdutytime').style.display = 'block';}
function showsfo()
{document.getElementById('divsfo').style.display = 'block';}
function showsfoadmin()
{document.getElementById('divsfoadmin').style.display = 'block';}	
function showsfostud()
{document.getElementById('divsfostud').style.display = 'block';}	
function ShowMarketing()
{document.getElementById('divmarketing').style.display = 'block';}
function ShowRecurrent()
{document.getElementById('divrecurrent').style.display = 'block';}	
function ShowOnAccount()
{document.getElementById('divonaccountreport').style.display = 'block';}
function ShowOnBlocked()
{document.getElementById('divonblocked').style.display = 'block';}
function ShowReceiptLogs()
{document.getElementById('divreceiptreport').style.display = 'block';}													
function HideAdministrator(){
	document.getElementById('divstudmenu').style.display = 'none';
	document.getElementById('divinsmenu').style.display = 'none';
	document.getElementById('divrequestform').style.display = 'none';
	document.getElementById('divmarketing').style.display = 'none';
	document.getElementById('divotherusers').style.display = 'none';
	//document.getElementById('divsms').style.display = 'none';
	document.getElementById('divonaccountreport').style.display = 'none';
	document.getElementById('divreceiptreport').style.display = 'none';
}
function HideSafety(){
	document.getElementById('divadminattendance_safety').style.display = 'none';
	document.getElementById('divstudmenu').style.display = 'none';
	document.getElementById('divinsmenu').style.display = 'none';
	document.getElementById('divrequestform').style.display = 'none';
	document.getElementById('divacmenu').style.display = 'none';
	document.getElementById('divsfoadmin').style.display = 'none';
	document.getElementById('divdaily').style.display = 'none';
}																																																	
function HideMe()
{
	document.getElementById('divstudmenu').style.display = 'none';
	document.getElementById('divinsmenu').style.display = 'none';
	document.getElementById('divrequestform').style.display = 'none';
	document.getElementById('div_gs_tki_report').style.display = 'none';
}
function HideMeIns()
{
	document.getElementById('divdailyins').style.display = 'none';
	document.getElementById('divrecurrent').style.display = 'none';
}
function HideMeChief()
{
	document.getElementById('divdaily').style.display = 'none';
}									
function HideMe2()
{
	document.getElementById('divcourse').style.display = 'none';
	document.getElementById('divexam').style.display = 'none';
	document.getElementById('divrequestform').style.display = 'none';
	document.getElementById('divsfostud').style.display = 'none'; 
}
function HideMe3()
{
	document.getElementById('divadminattendance').style.display = 'none';
	document.getElementById('divacmenu').style.display = 'none';
	document.getElementById('divdailymenu').style.display = 'none';
	document.getElementById('divdaily').style.display = 'none';
	document.getElementById('divsfoadmin').style.display = 'none';
	document.getElementById('div_gs_report').style.display = 'none';
	document.getElementById('div_gs_tki_report').style.display = 'none';
}												
function HideMeAccounts()
{
	<?php if($checkndex != 4081){?>
	document.getElementById('divreceiptreport').style.display = 'none';
	document.getElementById('divonaccountreport').style.display = 'none';
	document.getElementById('divstudmenu').style.display = 'none';
	document.getElementById('divinsmenu').style.display = 'none';
	<?php } ?>
	document.getElementById('divrequestform2').style.display = 'none';
	document.getElementById('divprocurement').style.display = 'none';
}
function HideMeStaff()
{document.getElementById('divrequestform2').style.display = 'none';}
function ShowDailyIns()
{document.getElementById('divdailyins').style.display = 'block';}			
</script>
<style type="text/css">
	td{padding:40px;}
	.nopadd{padding:1px 5px;color:#3485a4;}
	img{border-style:none;}
</style>
</head>
<?php
include "dblinklocal.php";
if(!empty($_GET)) extract($_GET);
if($questionid != "" && $questionactive == "1"){echo "<body onload='showquestion();'>";}
?>
<body>
<?php 
if($crypt_key == ''){include "encrypt2.php";}
/*********encryption*************************/
$l_secure_query = 'ndex='.$checkndex; 
$l_encrypted = doEncrypt($l_secure_query); 
/**********************************************/
if($loginerror == "1"){?>
<input class="lbOn" id="lbOnAuto" type="hidden" value="loginquestion.php?msg=username and password are not valid">
<?php } ?>
	<div class="Body">
    	<center>
    	<div class="pagseg">
        <?php 
		include "header2.php"; 
		if($opencon > 0 && $opencon2 == 0  && $dept != "1"){ ?>
        	<input class="lbOn" id="lbOnAuto" type="hidden" value="openconnection.php">
        <?php }
		if($opencon2 == 1){
			$_SESSION["opencon"]= 0;
			$opencon= 0;
        } 
		$QueryPolicy = mysql_num_rows(mysql_query("SELECT fldpage FROM tblpolicy WHERE fldpage = 'flight_ops_policy.php' AND flduserid = '$checkndex'"));
		if($dept == "1" && $QueryPolicy == 0 && $courseref != 17 && $courseref != 50){
			echo "<script LANGUAGE=\"JavaScript\">document.location.href ='flight_ops_policy.php'</script>";
			exit();
		}
		if($opencon2 == 1 && $signout == 1){
			$i = mysql_query("UPDATE tbl_login_logs SET loggedout_datetime = NOW() WHERE DATE(logged_datetime) = CURDATE() AND username = '$usernameo' AND usertable = '$usertableo' AND loggedout_datetime IS NULL AND log_id <> '$logid'");
        } 
		if($dept == "1i" && $flightins != ""){ 
			$QueryPending_FP = mysql_num_rows(mysql_query("SELECT flightplan_dept FROM tblflightplan WHERE flightplan_dept = '1' AND fldstatus = '0'"));
		}
		if($dept == "1i"){ 
			$CheckPendingDebrief1 = mysql_num_rows(mysql_query("SELECT A.ndex as flightID FROM tbltechlog A LEFT JOIN tbluserlogin B ON A.fldstudent=B.ndex  WHERE A.fldstudent > '0' AND A.fldduration > '0' AND A.fldstatusrecord = '0' AND A.fldteacher = $checkndex  AND A.fldplane != '22' AND B.fldlevel = '1' AND A.flddate > '2015-12-31' AND A.fldcourse NOT IN (0,21,62,63,64,65,80,81,82,83)"));
			$TotalPendingDebrief = $CheckPendingDebrief1 + $CheckPendingDebrief2;
		}
		if($dept == "1"){
			$QueryEmergencyDrills = mysql_num_rows(mysql_query("SELECT fldstudentid FROM tblemergency_drills WHERE fldstudentid = '$checkndex'"));
		}
		///////STUDENT LEAVE NOTIFICATION///////
		if($dept == "1i" || $dept == "1ie"){
			$QueryLeaveReq3 = mysql_num_rows(mysql_query("SELECT fldfirstapprovalstatus FROM tblstudent_leaverequest WHERE fldfirstapprovalstatus = '1' AND fldstatus = '0' AND fldsecondapprovalid ='$checkndex' AND fldsecondapprovalstatus = '0'"));
		}
		if($dept == "1i" || $dept == "1ie"){
			$QueryLeaveReq4 = mysql_num_rows(mysql_query("SELECT fldfirstapprovalstatus FROM tblstudent_leaverequest WHERE fldfirstapprovalstatus = '1' AND fldstatus = '0' AND fldsecondapprovalstatus = '1' AND fldthirdapprovalid ='$checkndex' AND fldthirdapprovalstatus = '0'",$conn));
		}
		///////STUDENT LEAVE NOTIFICATION///////
		if($dept == "Administrator"){
			$QueryPendingPassport = mysql_num_rows(mysql_query("SELECT fldaccountsstatus FROM tblpassportrequest WHERE fldaccountsstatus = '1' AND fldgmstatus = '0' AND fldstatus = '0'",$conn));
			$QueryLeaveReq = mysql_num_rows(mysql_query("SELECT flddeptchiefapproval FROM tblleaverequest  WHERE (flddeptchiefapproval = '1' AND fldaccountsstatus = '1' AND fldgmstatus='0' AND fldstatus='0') or (flddeptchiefapproval = '1' AND fldaccountsstatus = '0' AND fldgmstatus='0' AND fldstatus='0' AND fldrealdept = 'staff') order by ndex desc,fldstatus asc",$conn));
			$QueryLeaveReqHR = mysql_num_rows(mysql_query("SELECT flddeptchiefapproval FROM tblleaverequest  WHERE (flddeptchiefapproval = '1' AND fldaccountsstatus = '0' AND fldgmstatus='0' AND fldstatus='0') or (flddeptchiefapproval = '1' AND fldaccountsstatus = '0' AND fldgmstatus='0' AND fldstatus='0' AND fldrealdept = 'staff') order by ndex desc,fldstatus asc",$conn));
			$CheckPendingsEngrng = mysql_num_rows(mysql_query("SELECT fldengrapproval FROM tblsuppliersend WHERE fldengrapproval > '0' AND fldgmid = '0'",$conn));
			$CheckToBeFullRegistered1 = mysql_num_rows(mysql_query("SELECT flregistration_status FROM tblstudents WHERE  flregistration_status = '0' AND fldgm_status > '0' AND fldhot_ID > '0' AND fldaccountant_ID > '0' AND fldcourse != '17'",$conn));
			$CheckToBeFullRegistered2 = mysql_num_rows(mysql_query("SELECT tblstudents.flduserid FROM tblstudents LEFT JOIN tblcourse_approval ON tblstudents.flduserid = tblcourse_approval.fldstudent_id  WHERE tblcourse_approval.fldstatus = '0' AND tblcourse_approval.fldhot_approval > '1' AND tblcourse_approval.fldaccounts_approval = '1' AND tblcourse_approval.fldgm_id > '0' AND tblcourse_approval.fldcourse_id != '17'",$conn));
			$CheckToBeFullRegistered = $CheckToBeFullRegistered1 + $CheckToBeFullRegistered2;
			if($gm == "1"){
				$GMApprovalforApplicant = mysql_num_rows(mysql_query("SELECT fldgm_status FROM tblstudents WHERE fldgm_status = '0' AND fldhot_ID > '0' AND fldaccountant_ID > '0'",$conn));
				$GMApprovalforApplicant2 = mysql_num_rows(mysql_query("SELECT tblcourse_approval.fldhot_approval FROM tblstudents LEFT JOIN tblcourse_approval ON tblstudents.flduserid = tblcourse_approval.fldstudent_id  WHERE  tblcourse_approval.fldhot_approval = '1' AND tblcourse_approval.fldaccounts_approval > '0' AND tblcourse_approval. fldgm_id  = '0'",$conn));
				$GMApprovalforApplicant = $GMApprovalforApplicant + $GMApprovalforApplicant2;
			}
		}  
		if($dept == "Accounting"){
			$CheckPayMent = mysql_num_rows(mysql_query("SELECT S.ndex AS studndex FROM tblstudents S LEFT JOIN tblengineering_payment E ON E.flduserid = S.flduserid WHERE E.flddate <= '$mydate' AND E.fldaccountid = '0' AND S.fldstatus = '0'",$conn));
			$CheckPayMentPlanCreated = mysql_num_rows(mysql_query("SELECT E.flduserid FROM tblstudents S LEFT JOIN tblengineering_payment E ON E.flduserid = S.flduserid WHERE E.flduserid IS NULL AND S.fldcourse = '17' AND S.flregistration_status='1' AND S.fldstatus = '0' AND S.fldreal_sponsored = '0'",$conn));
			$QueryPendingPassport = mysql_num_rows(mysql_query("SELECT fldaccountsstatus FROM tblpassportrequest  WHERE (fldaccountsstatus = '0' AND fldcourse = '17' AND flddept_manager_status = '1' AND fldstatus != '4') or  (fldaccountsstatus = '0' AND fldcourse != '17' AND fldstatus != '4')",$conn));
			$QueryInitialPayment = mysql_num_rows(mysql_query("SELECT fldhot_ID FROM tblstudents WHERE  fldhot_ID > '0' AND fldaccountant_ID = '0'",$conn));
			$QueryInitialPayment2 = mysql_num_rows(mysql_query("SELECT C.fldhot_approval FROM tblstudents S LEFT JOIN tblcourse_approval C ON S.flduserid = C.fldstudent_id  WHERE  C.fldhot_approval = '1' AND C.fldaccounts_approval = '0'",$conn));
			$QueryInitialPayment3 = mysql_num_rows(mysql_query("SELECT EI.fldstatus FROM tblelp_examinees E LEFT JOIN tblelp_exam_info EI ON E.ndex = EI.fldexamineeid WHERE EI.fldstatus = '0' AND EI.fldaccountsid = '0'",$conn));
			$QueryInitialPayment = $QueryInitialPayment + $QueryInitialPayment2 + $QueryInitialPayment3;
			$CheckCourseAccountAvailable = mysql_num_rows(mysql_query("SELECT S.ndex FROM tblstudents S LEFT JOIN tblstudent_course_balance CB ON S.flduserid = CB.fldstudent_id WHERE S.`flddate` >= '2015-01-01' AND S.flduserid != '' AND S.`flregistration_status` = '1' AND S.`fldstatus` = '0' AND S.`fldcourse` != '17' AND CB.fldstudent_id IS NULL ORDER BY S.`flddate`",$conn));
			$CheckElpApplicants = mysql_num_rows(mysql_query("SELECT tblelp_examinees.ndex FROM tblelp_examinees LEFT JOIN tblelp_exam_info ON tblelp_examinees.ndex = tblelp_exam_info.fldexamineeid WHERE tblelp_exam_info.fldstatus = '0' AND tblelp_exam_info.fldaccountsid = '0'",$conn));
			$CheckOverdueFlights= mysql_num_rows(mysql_query("SELECT A.flddate,A.ndex as payment_ID  FROM tblengineering_payment A LEFT JOIN tblstudents B ON A.flduserid=B.flduserid WHERE B.fldstatus = '0' AND A.flddate <= CURDATE() AND  A.fldaccountid = '0' AND B.fldstatus = '0' AND fldemail_notif_overdue != '1' AND A.fldcourse > '0' AND A.fldcourse = '4' AND B.fldaccountnum != '123901' AND B.fldaccountnum != '124056' AND B.fldaccountnum != '124051'",$conn));
		} 
		if($chiefins == "1"){
			$CheckSkillTestReqCFI = mysql_num_rows(mysql_query("SELECT fldcfiid FROM tblskilltestrecommendation WHERE fldcfiid <= '0'",$conn));
			$QueryAlert = mysql_num_rows(mysql_query("SELECT fldstatus FROM tblalert  WHERE  fldstatus = 0 AND (part3_instructor IS NULL OR  part32_instructor IS NULL OR part4_instructor IS NULL)",$conn));
		}
		if($hot == "1"){
			$QueryLeaveReqfor_HOT = mysql_num_rows(mysql_query("SELECT flddeptchiefapproval FROM tblleaverequest  WHERE flddeptchiefapproval = '1' AND fldhot_approval = '0' AND fldstatus='0' AND fldaccountsstatus = '0' AND (fldrealdept = 'Chief' or fldrealdept = 'Ground_Admin' or fldrealdept = 'Flight_Ops' or fldrealdept = '1i')",$conn));	
			$QueryStudentApproval = mysql_num_rows(mysql_query("SELECT fldmedical_check FROM tblstudents WHERE  fldhot_ID = '0' AND fldcourse != '17' AND fldmedical_check = '1' ",$conn));
			$counter2 = mysql_num_rows(mysql_query("SELECT tblstudents.flduserid FROM tblstudents LEFT JOIN tblcourse_approval ON tblstudents.flduserid = tblcourse_approval.fldstudent_id  WHERE (tblstudents.fldfirstname like '%$searchnameid%' or tblstudents.fldlastname like '%$searchnameid%' or tblstudents.fldpassportnumber like '%$searchnameid%' or tblstudents.fldmobile like '%$searchnameid%') and tblcourse_approval.fldhot_approval = '' AND tblcourse_approval.fldcourse_id != '17' ",$conn));
			$QueryStudentApproval = $QueryStudentApproval + $counter2;
		}else if($dept == "1i" && $chiefins == "1")
		{ 
			$CheckUserPosition = mysql_query("SELECT fldchiefinstructor,fldhot,fldgroundinstructor,fldflightinstructor  FROM tbluserlogin WHERE ndex = '$checkndex'",$conn);
			while($dataCheckUser = mysql_fetch_array($CheckUserPosition))
			{
				$chiefinss = $dataCheckUser['fldchiefinstructor'];
				$hotins = $dataCheckUser['fldhot'];
				$QDeptGround = $dataCheckUser['fldgroundinstructor'];
				$QDeptFlight = $dataCheckUser['fldflightinstructor'];
			}
			
			if($chiefinss == "1" && $hotins != "1"){ 
				if($QDeptFlight != ""){
					$QueryLeave = mysql_query("SELECT fldrealdept,fldcreatedby FROM tblleaverequest WHERE flddeptchiefapproval = '0' AND fldstatus = '0' AND (fldrealdept = '1i' or fldrealdept = 'Flight_Ops'",$conn);
					while($DataLeave = mysql_fetch_array($QueryLeave)){
						$RealDept = $DataLeave['fldrealdept'];
						$CreatedBy = $DataLeave['fldcreatedby'];
						if($RealDept == "1i"){
							$QueryInstructorDept = mysql_num_rows(mysql_query("SELECT ndex FROM tbluserlogin WHERE fldflightinstructor = 'flightinstructor' AND ndex = '$CreatedBy'",$conn));
						}else{
							$QueryNotBaby = mysql_num_rows(mysql_query("SELECT ndex FROM tblusers WHERE ndex != '10' AND ndex = '$CreatedBy' AND flddept = 'Flight_Ops'",$conn));	
						}
						if($QueryInstructorDept > 0 || $QueryNotBaby > 0){
							$QueryLeaveReq++;
						}
					}
					$QueryExceedingApproval = mysql_num_rows(mysql_query("SELECT a.flduserid as flduseridd FROM tblapprovalexceedingdutytime a LEFT JOIN tbluserlogin b ON a.flduserid = b.ndex WHERE b.fldflightinstructor='flightinstructor' AND a.fldstatusapproval='0'",$conn));
				}
				if($QDeptGround != "" && $QDeptFlight == ""){ 
					$CheckOverdueFlights= mysql_num_rows(mysql_query("SELECT A.flddate FROM tblengineering_payment A LEFT JOIN tblstudents B ON A.flduserid=B.flduserid WHERE B.fldstatus = '0' AND A.flddate <= CURDATE() AND  A.fldaccountid = '0' AND B.fldstatus = '0' AND fldemail_notif_overdue != '1' AND A.fldcourse > '0' AND A.fldcourse = '4'",$conn));
					$QueryLeave = mysql_query("SELECT fldrealdept,fldcreatedby FROM tblleaverequest WHERE flddeptchiefapproval = '0' AND fldstatus = '0' AND (fldrealdept = '1i' or fldrealdept = 'Ground_Admin')",$conn);
					while($DataLeaveReq = mysql_fetch_array($QueryLeave)){
						$RealDept = $DataLeaveReq['fldrealdept'];
						$CreatedBy = $DataLeaveReq['fldcreatedby'];
						if($RealDept == "1i"){
							$QueryInstructorDept = mysql_num_rows(mysql_query("SELECT ndex FROM tbluserlogin WHERE fldgroundinstructor = 'groundinstructor' AND fldflightinstructor = '' AND ndex = '$CreatedBy'",$conn));
						}else{
							$QueryNotBaby = mysql_num_rows(mysql_query("SELECT ndex FROM tblusers WHERE ndex = '10' AND ndex = '$CreatedBy' AND flddept = 'Ground_Admin'",$conn));
						}
						if($QueryInstructorDept > 0 || $QueryNotBaby > 0){$QueryLeaveReq++;}
					}
				}
			}else{
				$QueryLeaveReq = mysql_num_rows(mysql_query("SELECT fldstatus FROM tblleaverequest  WHERE flddeptchiefapproval = '0' AND fldstatus='0' AND fldrealdept = 'Chief' order by ndex desc,fldstatus asc",$conn));
			}
			if($sfo == 1){
				$QuerySFO = mysql_num_rows(mysql_query("SELECT fldfsousername FROM tblsafetyreport1 WHERE fldfsousername = ''",$conn));
				$QuerySFO2 = mysql_num_rows(mysql_query("SELECT fldremarks FROM tblflightsafetyreport2 WHERE fldremarks = ''",$conn));
			}
		}
		if($dept == "Administrator" || $dept == "Asst. Administrator" || $dept == "Admin/Engineering"  || $dept == "Admin/Flights"){$dept_leave_request = "Administrator";}
		if($dept == "Engineering" || $dept == "Asst. Engineering"){$dept_leave_request = "Engineering Maintenance";}
		if($dept == "Accounting"){$dept_leave_request = "Accounts";}
		if($dept == "Safety"){$dept_leave_request = "Safety";}	
		if($dept == "1i" && $flightins == "flightinstructor"){$dept_leave_request = "Flight Opertation";}
		if($dept == "1i" && $groundins == "groundinstructor" && $flightins == ""){$dept_leave_request = "Ground School";}	
		if($dept == "1ie"){$dept_leave_request = "AMEC";}		
		$CheckingLeaveRequestRequiredApproval = mysql_num_rows(mysql_query("SELECT firstapprovalid FROM tblleaverequest WHERE (firstapprovalid  = '$checkndex' AND firstapprovaldept = '$dept_leave_request' AND firstapproval_status = '' AND fldstatus = '0') or (firstapprovalid > '0' AND firstapproval_status = '1' AND secondapprovaldept = '$dept_leave_request' AND secondapprovalid = '$checkndex' AND secondapproval_status = '' AND fldstatus = '0')  or (firstapprovalid = '0' AND firstapproval_status = '' AND secondapprovaldept = '$dept_leave_request' AND secondapprovalid = '$checkndex' AND secondapproval_status = '' AND fldstatus = '0') or (firstapprovalid  > '0' AND firstapproval_status = '1' AND secondapprovalid > '0' AND secondapproval_status = '1' AND thirdapproval_status = '' AND thirdapprovalid = '$checkndex' AND thirdapprovaldept = '$dept_leave_request' AND fldstatus = '0')  or (firstapprovalid  = '0' AND firstapproval_status = '' AND secondapprovalid > '0' AND secondapproval_status = '1' AND thirdapproval_status = '' AND thirdapprovalid = '$checkndex' AND thirdapprovaldept = '$dept_leave_request' AND fldstatus = '0')  or (firstapprovalid  > '0' AND firstapproval_status = '1' AND secondapprovalid = '0' AND secondapproval_status = '' AND thirdapprovalid > '0' AND thirdapproval_status = '' AND thirdapprovalid = '$checkndex' AND firstapprovaldept = '$dept_leave_request' AND fldstatus = '0') or (firstapprovalid  = '0' AND firstapproval_status = '' AND secondapprovalid = '0' AND secondapproval_status = '' AND thirdapproval_status = '' AND thirdapprovalid = '$checkndex' AND thirdapprovaldept = '$dept_leave_request' AND fldstatus = '0')",$conn));
		if($dept == "1i" || $dept == "1ie"){$table_source = "tbluserlogin";}
		else{$table_source = "tblusers";}
		$CheckAuditConfirmation = mysql_num_rows(mysql_query("SELECT fldconfirmation_status FROM tblquality_audit WHERE fldconfirmation_status = '0' AND fldauditee_tblsource = '$table_source' AND fldauditees = '$checkndex'",$conn));
		$CheckAuditRequestChangeDate = mysql_num_rows(mysql_query("SELECT fldconfirmation_status FROM tblquality_audit WHERE fldconfirmation_status = '2' AND fldcreated_by = '$checkndex'",$conn));
		$QueryAlert = mysql_num_rows(mysql_query("SELECT fldstatus FROM tblalert  WHERE  fldstatus = 0 AND (part3_instructor IS NULL OR  part32_instructor IS NULL OR part4_instructor IS NULL) ORDER BY alert_id DESC",$conn));
		if($QueryPendingPassport > 0 || $QueryExceedingApproval > 0 || $CheckPendingsEngrng > 0 || $QuerySFO > 0 || $QuerySFO2 > 0 || $QueryPending_FP > 0 || $CheckingLeaveRequestRequiredApproval > 0 || $CheckPayMent > 0 || $CheckPayMentPlanCreated > 0 || $QueryEmergencyDrills > 0 || $CheckSkillTestReqCFI > 0 || $QueryLeaveReq3 > 0 || $QueryLeaveReq4 > 0 || $QueryStudentApproval > 0 || $QueryInitialPayment > 0 || $GMApprovalforApplicant > 0 || $CheckCourseAccountAvailable > 0 || $CheckElpApplicants > 0 || $CheckToBeFullRegistered > 0 || $TotalPendingDebrief > 0 || $CheckAuditConfirmation > 0 || $CheckAuditRequestChangeDate > 0 || $QueryAlert > 0 || $CheckOverdueFlights > 0){
			if($cancel != "1" && $checkndex == 3906 && $mydate == "2022-02-26"){?>	
            <input class="lbOn" id="lbOnAuto" type="hidden" value="birthday.php">
        <?php }
			else if($cancel != "1"){?>	
            <input class="lbOn" id="lbOnAuto" type="hidden" value="pendingapproval.php">
        <?php }
		} 
		$defstr = "123";
		$defpassword = md5($defstr);
		if($dept == "Administrator" || $dept == "Accounting" || $dept == "Asst. Administrator" || $dept == "Engineering" || $dept == "Asst. Engineering Parts" || $dept == "Engineering Instructors" || $dept == "Staff" || $dept == "Asst. Engineering"  || $dept == "Admin/Flights"  || $dept == "Safety"){
			$CheckPassword = mysql_query("SELECT fldpassword,fldusername FROM tblusers WHERE ndex = '$checkndex'",$conn);
			while($DataPassword = mysql_fetch_array($CheckPassword)){
				$userpassword = $DataPassword['fldpassword'];
				$userusername = $DataPassword['fldusername'];
			}
		}
		if($dept == "1i" || $dept == "1"){
			$CheckPassword = mysql_query("SELECT fldpassword,fldusername FROM tbluserlogin WHERE ndex = '$checkndex'",$conn);
			while($DataPassword = mysql_fetch_array($CheckPassword)){
				$userpassword = $DataPassword['fldpassword'];
				$userusername = $DataPassword['fldusername'];
			} 
		}
		if($userpassword == $defpassword){ ?>
        <input class="lbOn" id="lbOnAuto" type="hidden" value="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex;?>&username=<?php echo $userusername;?>&password=<?php echo $userpassword;?>">
        <?php } ?>
            <div class="mainbody">
            	<div class="mainmenu">
                	<div style="width:20%;height:100%;background-color:#cfe9f2;"></div>
                    <div style="width:80%;height:100%;">
                        <div style="height:60px; vertical-align:central;font-weight:bold;color:white;padding-left:50px;"><?php echo date('l d/m/Y',strtotime($mydate)); ?>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <a href="directory.php"><img src="image/Contacts.png" width="25" height="25"></a> <a href="directory.php" style="color:#b1e1f7;text-decoration:none;" target="_blank">Contact Directory</a> &nbsp; &nbsp; <a href="annualbirthday.php"><img src="image/bday.png" width="25" height="25"></a> <a href="annualbirthday.php" style="color:#b1e1f7;text-decoration:none;" target="_blank">Birthday Directory</a>&nbsp; &nbsp; <a href="monthlybirthday.php"><img src="image/bday.png" width="25" height="25"></a> <a href="monthlybirthday.php" style="color:#b1e1f7;text-decoration:none;" target="_blank"><?php echo date("F");?> Celebrants</a>
                        </div>
                    </div>
                </div>
                <div style="width:100%;">
                	<?php if($dept == "Admin/Flights"){?>
               		<div style="width:20%;height:400px;border-right:solid 1px #8dcae3;">
                        <table>
                            <tr>
                                <td class="nopadd" width="10">
                                    <a href="otherusers_view.php?<?php echo $l_encrypted;?>" style="cursor:pointer;font-size:12px;"><img src="image/folder.png"  style="width:14px;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                    <a  style="cursor:pointer;font-size:12px;" onclick="location.href='otherusers_view.php?<?php echo $l_encrypted;?>'">My Profile</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10" id="studentslink">
                                    <img src="image/folder.png"  style="width:14px;" onclick="HideAdministrator();showstudmenu();" style="cursor:pointer;">
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                    <a onclick="HideAdministrator();showstudmenu();" style="cursor:pointer;font-size:12px;">Student</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" style="padding:0px"></td>
                                <td class="nopadd" style="padding:0px">
                                <div style="display:none;" id="divstudmenu">
                                    <table>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="allselect.php" style="color:#3485a4;text-decoration:none;">All Student</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="studselect.php" style="color:#3485a4;text-decoration:none;">Current Student</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="pendingstudent.php" style="color:#3485a4;text-decoration:none;">Pending Student</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="incompleteselect.php" style="color:#3485a4;text-decoration:none;">Unaccomplished Student</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="accomplishselect.php" style="color:#3485a4;text-decoration:none;">Accomplished Student</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="stud_feedback.php?view=3" style="color:#3485a4;text-decoration:none;">Student Feedback</a></td>
                                        </tr>
                                    </table>
                                </div>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10" id="intructorslink">
                                    <img src="image/folder.png"  style="width:14px;" onclick="HideAdministrator();showinsmenu();" style="cursor:pointer;">
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                    <a onclick="HideAdministrator();showinsmenu();" style="cursor:pointer;font-size:12px;">Instructor</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='student_attendance_all_with_date.php'">Attendance</a>                                     
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" style="padding:0px"></td>
                                <td class="nopadd" style="padding:0px">
                                <div style="display:none;" id="divinsmenu">
                                    <table>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="insselect.php" style="color:#3485a4;text-decoration:none;">Current Instructor</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="pilotstatus.php" style="color:#3485a4;text-decoration:none;" target="_blank">Pilot's Status</a></td>
                                        </tr>
                                       	<tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="addins.php" style="color:#3485a4;text-decoration:none;">Add New Instructor</a></td>
                                        </tr>
                                    </table>
                                </div>
                                </td>
                        	</tr>
                            <tr>
                                <td class="nopadd" width="10">
                                    <a  style="cursor:pointer;font-size:12px;" href="studentdocstatus.php"><img src="image/folder.png"  style="width:14px;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                    <a  style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="studentdocstatus.php">Student Document Status</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10" id="reqadmin">
                                    <img src="image/folder.png"  style="width:14px;" onclick="HideAdministrator();showrequest();" style="cursor:pointer;">
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                    <a onclick="HideAdministrator();showrequest();" style="cursor:pointer;font-size:12px;">Request Form</a>
                                </td>
                            </tr>
                             <tr>
                                <td class="nopadd" style="padding:0px"></td>
                                <td class="nopadd" style="padding:0px">
                                <div id="divrequestform" style="display:none;">
                                    <table>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd">
                                                <a href="passportreq.php" style="color:#3485a4;text-decoration:none;">Request for passport</a>
                                            </td>
                                        </tr>
                                        <?php if($dept == "Admin/Flights"){?>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd">
                                                <a href="passportreqapprovagml.php" style="color:#3485a4;text-decoration:none;">Passport Request Approval</a>
                                            </td>
                                        </tr>
                                          <?php } ?>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd">
                                                <a href="leavereq.php" style="color:#3485a4;text-decoration:none;" target="_blank">Request for Leave</a>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd">
                                                <a href="leavereqgm.php" style="color:#3485a4;text-decoration:none;" target="_blank">Leave Request Approval</a>
                                            </td>
                                        </tr>
                                    </table>
                                    </div>
                                </td>
                            </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin">
                                    	<a style="cursor:pointer;font-size:12px;text-decoration:none" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex; ?>&username=<?php echo $userusername; ?>&password=<?php echo $userpassword; ?>&userdecided=1" class="lbOn"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showrequest();" style="cursor:pointer;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;">
                                    	<a style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex;?>&username=<?php echo $userusername; ?>&password=<?php echo $userpassword; ?>&userdecided=1" class="lbOn">Change Password</a>
                                    </td>
                                </tr>
                      		</table>
                    </div> 
                    <?php 
					}
					if($dept == "Safety"){?>
               		<div style="width:20%;height:400px;border-right:solid 1px #8dcae3;">
                        	<table>
                            	   <!--tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='otherusers_view.php?<?php echo $l_encrypted;?>'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='otherusers_view.php?<?php echo $l_encrypted;?>'">My Profile</a>
                                    </td>
                                </tr-->
                            	 <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" href="employee_file.php?ndex=<?php echo $checkndex; ?>&sel_dept=8"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;" href="employee_file.php?ndex=<?php echo $checkndex; ?>&sel_dept=8">My HR Profile</a>
                                    </td>
                                </tr>
								<?php /* Start of Menu for HR Employee File for Capt. Riad*/
                                if($checkndex == 111)
								{?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideAdministrator();showotherhremp();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideAdministrator();showotherhremp();" style="cursor:pointer;font-size:12px;">HR Employee File</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divotherhremp">
                                    	<table>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=11" style="color:#3485a4;text-decoration:none;">Management</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=1" style="color:#3485a4;text-decoration:none;">Administration</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=2" style="color:#3485a4;text-decoration:none;">Accounts</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=10" style="color:#3485a4;text-decoration:none;">Marketing</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=3" style="color:#3485a4;text-decoration:none;">Aircraft Maintenance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=5" style="color:#3485a4;text-decoration:none;">Maintenance Engineering Training</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=12" style="color:#3485a4;text-decoration:none;">Flight Operations</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=6" style="color:#3485a4;text-decoration:none;">Flight Training</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=14" style="color:#3485a4;text-decoration:none;">Flight Training (A) Flight</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=13" style="color:#3485a4;text-decoration:none;">Flight Training (H) Flight</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=7" style="color:#3485a4;text-decoration:none;">Flight Training Ground School</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=8" style="color:#3485a4;text-decoration:none;">Safety And Quality Assurance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=9" style="color:#3485a4;text-decoration:none;">IT</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=4" style="color:#3485a4;text-decoration:none;">Support Staffs</a></td>
                                            </tr> 
                                       	</table>
                                       </div>
                                    </td>
                                </tr>
                                <?php 
								}
								/* End of Menu for HR Employee File (Capt. Riad) */
                                ?>
                                 <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='view_zone.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='view_zone.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">New Dawn Zone Status</a>
                                    </td>
                                </tr>
                            	<tr>
                                	<td class="nopadd" width="10" id="studentslink">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideSafety();showstudmenu();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideSafety();showstudmenu();" style="cursor:pointer;font-size:12px;">Student</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divstudmenu">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="allselect.php" style="color:#3485a4;text-decoration:none;">All Student</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="studselect.php" style="color:#3485a4;text-decoration:none;">Current Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="pendingstudent.php" style="color:#3485a4;text-decoration:none;">Pending Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="incompleteselect.php" style="color:#3485a4;text-decoration:none;">Unaccomplished Student</a></td>
                                            </tr>
     	                                       <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="accomplishselect.php" style="color:#3485a4;text-decoration:none;">Accomplished Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="stud_feedback.php?view=3" style="color:#3485a4;text-decoration:none;">Student Feedback</a></td>
                                            </tr>
                                        </table>
                                       </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="intructorslink">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideSafety();showinsmenu();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideSafety();showinsmenu();" style="cursor:pointer;font-size:12px;">Instructor</a>
                                    </td>
                                </tr>
                                 <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divinsmenu">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="insselect.php" style="color:#3485a4;text-decoration:none;">Current Instructor</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="pilotstatus.php" style="color:#3485a4;text-decoration:none;" target="_blank">Pilot's Status</a></td>
                                            </tr>
                                           <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="addins.php" style="color:#3485a4;text-decoration:none;">Add New Instructor</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report"><img src="image/folder.png"  style="width:14px;cursor:pointer;" onclick="show_gs_report();"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="show_gs_report();" style="cursor:pointer;font-size:12px;">Student Theoretical Progress Report</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div  id="div_gs_report" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="gs_report.php" target="_blank">Examination Summary</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="studentprogress_report_gs.php" style="color:#3485a4;text-decoration:none;" target="_blank">Student Progress Report</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="gs_quizreport.php" target="_blank">Quizzes Summary</a></td>
                                            </tr>
                                       	</table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><img src="image/folder.png"  style="width:14px;" onclick="HideSafety();showrequest();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideSafety();showrequest();" style="cursor:pointer;font-size:12px;">Request Form</a></td>
                                </tr>
                                 <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div id="divrequestform" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="passportreq.php" style="color:#3485a4;text-decoration:none;">Request for passport</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="passportreqapprovagml.php" style="color:#3485a4;text-decoration:none;">Passport Request Approval</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="leavereq.php" style="color:#3485a4;text-decoration:none;">Request for Leave</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="leavereqgm.php" style="color:#3485a4;text-decoration:none;" target="_blank">Leave Request Approval</a></td>
                                            </tr>
                                        </table>
                                    </div>
                                    </td>
                                </tr>
                                <?php /* Start of Menu for SMS Attendance (Capt. Riad) */
								if($checkndex == 111)
								{?>
                                <tr>
                                	<td class="nopadd" width="10"><a href="sms_attendance.php" style="cursor:pointer;font-size:12px;"><img src="image/folder.png" style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="sms_attendance.php" style="cursor:pointer;font-size:12px;">SMS Attendance</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='reporting_system.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='reporting_system.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Reporting System</a>
                                    </td>
                                </tr>
                                <?php } 
								/* End of Menu for SMS Attendance (Capt. Riad) */
								?>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin">
                                    	<a style="cursor:pointer;font-size:12px;text-decoration:none" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex;?>&username=<?php echo $userusername;?>&password=<?php echo $userpassword;?>&userdecided=1" class="lbOn"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showrequest();" style="cursor:pointer;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;">
                                    <a style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex;?>&username=<?php echo $userusername;?>&password=<?php echo $userpassword;?>&userdecided=1" class="lbOn">Change Password</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="HideSafety();showacmenu();"><img src="image/folder.png"  style="width:14px;"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="HideSafety();showacmenu();">Aircraft</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divacmenu">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="aircraft.php" style="color:#3485a4;text-decoration:none;">Aircraft Maintenance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="aircraftattachments.php" style="color:#3485a4;text-decoration:none;">Aircraft Doc</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='accounting.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='accounting.php'">Flight Logs</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='showsched.php'" target="_blank"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='showsched.php'" target="_blank">Daily Schedule</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideSafety();showdaily();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideSafety();showdaily();" style="cursor:pointer;font-size:12px;">Reports</a>
                                    </td>
                                </tr>
                                 <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div  id="divdaily" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flight_course_flow_report.php" style="color:#3485a4;text-decoration:none;" target="_blank">Flight Course Flow Report</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="dailyflyingplanningreport.php" style="color:#3485a4;text-decoration:none;">Planning & Achievement Report</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flyingrecord.php" style="color:#3485a4;text-decoration:none;" target="_blank">Daily Record</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="instructorsreport.php" style="color:#3485a4;text-decoration:none;" target="_blank">Instructors Report</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd">
                                                	<!--a href="safetyreport1.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 1</a-->
                                                    <a href="aftermission_inside.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 1</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport2.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 2</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport1view.php" style="color:#3485a4;text-decoration:none;">View Flight Safety Report</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="view_aftermission_report.php?report_type=safety report" style="color:#3485a4;text-decoration:none;">View After Mission/Incident/Accident Report</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport2view.php" style="color:#3485a4;text-decoration:none;">View Share Your Experience</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flightsperday.php" style="color:#3485a4;text-decoration:none;">Flight Hours</a></td>
                                            </tr>
                                            
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report2">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideSafety();showdaily();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideSafety();showsfoadmin();" style="cursor:pointer;font-size:12px;">Flight Safety Reports</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div  id="divsfoadmin" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="view_aftermission_report.php?report_type=safety report" style="color:#3485a4;text-decoration:none;">View After Mission/Incident/Accident Report</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="view_birdstrike_report.php?report_type=safety report" style="color:#3485a4;text-decoration:none;">View Bird Strike and Wildlife Report</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="view_flight_safety_report.php?report_type=safety report" style="color:#3485a4;text-decoration:none;">View Safety Note</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="view_flight_safety_report.php?report_type=occurence report" style="color:#3485a4;text-decoration:none;">View Voluntary Occurence Report</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="view_flight_safety_report.php?report_type=hazard report" style="color:#3485a4;text-decoration:none;">View Hazard Report</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="view_operation_daily_report.php" style="color:#3485a4;text-decoration:none;">View Operation Daily Report</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport1view.php" style="color:#3485a4;text-decoration:none;">View Flight Safety Report 1</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport2view.php" style="color:#3485a4;text-decoration:none;">View Share Your Experience</a></td>
                                                
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report2">
                                    	<a href="add_notams.php"><img src="image/folder.png"  style="width:14px;" onclick="HideSafety();showdaily();" style="cursor:pointer;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="add_notams.php" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Notams Update</a>
                                    </td>
                                    
                                </tr>
                                <!--tr>
                                	<td class="nopadd" width="10" id="reqadmin"><a style="cursor:pointer;font-size:12px;text-decoration:none" href="studentprogress_new.php"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="studentprogress_new.php">SPMS</a>
                                    </td>
                                </tr-->
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="HideSafety();showadminattendance_safety();"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="HideSafety();showadminattendance_safety();">Student Attendance</a>
                                    </td>
                                </tr> 
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divadminattendance_safety">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_view.php" style="color:#3485a4;text-decoration:none;">Student Daily Attendance </a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_subjects.php" style="color:#3485a4;text-decoration:none;">Subject Attendance</a></td>
                                            </tr>
                                            
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_all.php" style="color:#3485a4;text-decoration:none;">Course Attendance </a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_all_with_date.php" style="color:#3485a4;text-decoration:none;">Total Student Attendance Hourse Monitoring</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_all_with_date_new.php" style="color:#3485a4;text-decoration:none;">Total Theoretical Classes Conducted</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>  
                                <tr>
                                	<td class="nopadd" width="10"><a href="safety_publish.php"  style="cursor:pointer;font-size:12px;"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="safety_publish.php"  style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Safety Publishes and Training</a>
                                    </td>
                                </tr>                       
							<?php  
							/* Start of Menu for Authorization */
							if($checkndex == 182 || $checkndex == 3940) // For Elias Talj only
							{?>
							<tr>
								<td class="nopadd" width="10">
									<img src="image/folder.png"  style="width:14px;" onclick="location.href='authorization_code.php'" style="cursor:pointer;">
								</td>
								<td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
									<a  onclick="location.href='authorization_code.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Quality Authorization</a>
								</td>
							</tr>
							<?php
                                  } if($auditees_session > 0 || $lead_auditor_session > 0 || $qam > 0){?>
                               	<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='quality_audit.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='quality_audit.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Quality Audit</a>
                                    </td>
                                </tr>
                                <?php } ?>
                             </table>
                    </div> 
                	<?php } if($dept == "Administrator"){?>
               		<div style="width:20%;height:400px;border-right:solid 1px #8dcae3;">
                        	<table>
                            	 <!--tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='otherusers_view.php?<?php echo $l_encrypted; ?>'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='otherusers_view.php?<?php echo $l_encrypted; ?>'">My Profile</a>
                                    </td>
                                </tr-->
                            	 <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" href="employee_file.php?ndex=<?php echo $checkndex; ?>&sel_dept=1"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;" href="employee_file.php?ndex=<?php echo $checkndex; ?>&sel_dept=1">My HR Profile</a>
                                    </td>
                                </tr>
								<?php /* Start of Menu for HR Employee File  (Tyron,Jeza,Dan,Hanan,Capt.Yahya) */
								//if($checkndex == 159 || $checkndex == 3915 || $checkndex == 3997 || $checkndex == 4014  || $checkndex == 28)
								$privilege2 = array(159,3915,3997,4014,28,4062,81,3984,4061,4055,4083,136,4007,4058,4093,3987,4110,4111,4105); // Tyron,Jeza,Dan,Hanan,Capt.Yahya,Sara,Jonalyn,Jill,Jane,NazzerAdminFlight,Brandi,Ahlam,Emelle,Alyaa,Thuriya,Shamsa,John,Maryam,Nadyah
								if(in_array($checkndex, $privilege2))
								{?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideAdministrator();showotherhremp();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideAdministrator();showotherhremp();" style="cursor:pointer;font-size:12px;">HR Employee File</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divotherhremp">
                                    	<table>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=11" style="color:#3485a4;text-decoration:none;">Management</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=1" style="color:#3485a4;text-decoration:none;">Administration</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=2" style="color:#3485a4;text-decoration:none;">Accounts</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=10" style="color:#3485a4;text-decoration:none;">Marketing</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=3" style="color:#3485a4;text-decoration:none;">Aircraft Maintenance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=5" style="color:#3485a4;text-decoration:none;">Maintenance Engineering Training</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=12" style="color:#3485a4;text-decoration:none;">Flight Operations</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=6" style="color:#3485a4;text-decoration:none;">Flight Training</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=14" style="color:#3485a4;text-decoration:none;">Flight Training (A) Flight</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=13" style="color:#3485a4;text-decoration:none;">Flight Training (H) Flight</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=7" style="color:#3485a4;text-decoration:none;">Flight Training Ground School</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=8" style="color:#3485a4;text-decoration:none;">Safety And Quality Assurance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=9" style="color:#3485a4;text-decoration:none;">IT</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=4" style="color:#3485a4;text-decoration:none;">Support Staffs</a></td>
                                            </tr> 
                                       	</table>
                                       </div>
                                    </td>
                                </tr>
                                <?php 
								}
								/* End of Menu for HR Employee File (Tyron,Jeza,Dan,Hanan,Capt.Yahya) */
                                ?>
                                <?php /* Start of Menu for SMS Attendance (Tyron,Jeza,Sara) */
								if($checkndex == 159 || $checkndex == 3915 || $checkndex == 4062)
								{?>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='sms_attendance.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='sms_attendance.php'">SMS Attendance</a>
                                    </td>
                                </tr>
                                <?php 
								}
								/* Start of Menu for Aircraft Type Technical Attendance  (Tyron,Jeza) */
								if($checkndex == 159 || $checkndex == 3915 || $checkndex == 28)
								{?>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='actt_attendance.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='actt_attendance.php'">Aircraft Type Technical Student Attendance</a>
                                    </td>
                                </tr>
								<?php }
								/* Start of Menu for Aircraft Type Technical Attendance  (Tyron,Jeza) */
								if($checkndex == 159 || $checkndex == 3915)
								{?>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='stud_quiz.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='stud_quiz.php'">Student Quiz</a>
                                    </td>
                                </tr>
								<?php }
								/* Start of Menu for Aircraft Type Technical Attendance  (Tyron,Jeza) */
								if($checkndex == 159 || $checkndex == 3915 || $checkndex == 190 || $checkndex == 28)
								{?>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='mt.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='mt.php'">Maintenance Tracking</a>
                                    </td>
                                </tr>
								<?php }
								/* Start of Menu for Aircraft Type Technical Attendance  (Tyron,Jeza,Jill, Yahya) */
								if($checkndex == 159 || $checkndex == 3915 || $checkndex == 3984 || $checkndex == 28)
								{?>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='ctr_view.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='ctr_view.php'">Maintenance Continuation Training Records</a>
                                    </td>
                                </tr>
								<?php } ?>
                            	<tr>
                                	<td class="nopadd" width="10" id="studentslink">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showstudmenu();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe3();HideMe();showstudmenu();" style="cursor:pointer;font-size:12px;">Student</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divstudmenu">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="allselect.php" style="color:#3485a4;text-decoration:none;">All Student</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="studselect.php" style="color:#3485a4;text-decoration:none;">Current Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="pendingstudent.php" style="color:#3485a4;text-decoration:none;">Pending Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="incompleteselect.php" style="color:#3485a4;text-decoration:none;">Unaccomplished Student</a></td>
                                            </tr>
     	                                       <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="accomplishselect.php" style="color:#3485a4;text-decoration:none;">Accomplished Student</a></td>
                                            </tr>
                                            </tr>
     	                                       <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="user_reset.php" style="color:#3485a4;text-decoration:none;">Reset Student Password</a></td>
                                            </tr>
											<?php 
                                            /* Start of Menu for Adding New Student for New Dawn only - Activated for France and Judee */
                                            if($checkndex == 3915 || $checkndex == 159)
                                            {?>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="addstud.php" style="color:#3485a4;text-decoration:none;">Add New Student Record</a></td>
                                            </tr>
                                            <?php } ?>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="admin_addstudent_new_course.php" style="color:#3485a4;text-decoration:none;">Add New Course To Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="course_schedule_summary.php" style="color:#3485a4;text-decoration:none;">Course Schedule Yearly Summary</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="stud_feedback.php?view=3" style="color:#3485a4;text-decoration:none;">Student Feedback</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="studentgatepassexpiry.php" style="color:#3485a4;text-decoration:none;">Student Document Expired</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="studentdocstatus.php" style="color:#3485a4;text-decoration:none;">Student Document Status</a></td>
                                            </tr>
                                        </table>
                                       </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="intructorslink">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showinsmenu();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe3();HideMe();showinsmenu();" style="cursor:pointer;font-size:12px;">Instructor</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divinsmenu">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="insselect.php" style="color:#3485a4;text-decoration:none;">Current Instructor</a></td>
                                            </tr>
                                            
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="pilotstatus.php" style="color:#3485a4;text-decoration:none;" target="_blank">Pilot's Status</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flyingrecord_ins.php" style="color:#3485a4;text-decoration:none;" target="_blank">Pilot's Daily Flying Record</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="resignedselect.php" style="color:#3485a4;text-decoration:none;" target="_blank">Resigned Instructor</a></td>
                                            </tr>
                                           <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="addins.php" style="color:#3485a4;text-decoration:none;">Add New Instructor</a></td>
                                            </tr>
                                           <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="dutytimefi_new.php" style="color:#3485a4;text-decoration:none;">Instructor Duty Time</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="studentslink">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideAdministrator();showotherusers();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideAdministrator();showotherusers();" style="cursor:pointer;font-size:12px;">Other Users</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divotherusers">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="addusers.php" style="color:#3485a4;text-decoration:none;">Add User (Staff)</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="addusers_outsiders.php" style="color:#3485a4;text-decoration:none;">Add User (Outsiders)</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users.php?sel_dept=0" style="color:#3485a4;text-decoration:none;">View All Users</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users.php?sel_dept=1" style="color:#3485a4;text-decoration:none;">View Administration</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users.php?sel_dept=2" style="color:#3485a4;text-decoration:none;">View Accounts</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users.php?sel_dept=3" style="color:#3485a4;text-decoration:none;">View Engineering</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users.php?sel_dept=4" style="color:#3485a4;text-decoration:none;">View Others</a></td>
                                            </tr>
                                       	</table>
                                       </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="HideMe3();HideMe();showacmenu();"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="HideMe3();HideMe();showacmenu();">Aircraft</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divacmenu">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="aircraft.php" style="color:#3485a4;text-decoration:none;">Aircraft Maintenance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="aircrafts_maintenace_report_yearly.php" style="color:#3485a4;text-decoration:none;">Aircraft On Ground</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="aircraftattachments.php" style="color:#3485a4;text-decoration:none;">View Aircraft Doc</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="aircarftattachements.php" style="color:#3485a4;text-decoration:none;">Upload Aircraft Doc</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="aircraftparts.php" style="color:#3485a4;text-decoration:none;">Aircraft Store</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="plane_dailylogs.php" style="color:#3485a4;text-decoration:none;">Aircraft Status</a></td>
                                            </tr>
                                             <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="aircraftdata.php" style="color:#3485a4;text-decoration:none;">Aircraft Data</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="c208_engine_dailystatus.php" style="color:#3485a4;text-decoration:none;">C208 Engine Daily Status</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="HideMe3();HideMe();showadminattendance();"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="HideMe3();HideMe();showadminattendance();">Student Attendance</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divadminattendance">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_view.php" style="color:#3485a4;text-decoration:none;">Student Daily Attendance </a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_subjects.php" style="color:#3485a4;text-decoration:none;">Subject Attendance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_all.php" style="color:#3485a4;text-decoration:none;">Course Attendance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_all_with_date.php" style="color:#3485a4;text-decoration:none;">Total Student Attendance Hours Monitoring</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_all_with_date_new.php" style="color:#3485a4;text-decoration:none;">Total Theoretical Classes Conducted</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();show_gs_report();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe3();HideMe();show_gs_report();" style="cursor:pointer;font-size:12px;">Student Theoretical Progress Report</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div  id="div_gs_report" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="gs_report.php" target="_blank">Examination Summary</a></td>
                                            </tr>
                                        	<!--tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="gs_report_per_student.php">Ground Record Per Student</a></td>
                                            </tr-->
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="studentprogress_report_gs.php" style="color:#3485a4;text-decoration:none;" target="_blank">Student Progress Report</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="gs_quizreport.php" target="_blank">Quizzes Summary</a></td>
                                            </tr>
                                        	<!--tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="studentexamstatus.php">GCAA Exam Completion</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="studentexamflystatus.php">GCAA Examination Expiry</a></td>
                                            </tr-->
                                       	</table>
                                        </div>
                                    </td>
                                </tr>
                                <?php 
								/* Start of Menu for Employee Attendance for All */
								if($checkndex == 159 || $checkndex == 3915 || $checkndex == 3997 || $checkndex == 4014 || $checkndex == 4093)
								{?>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;"><img src="image/folder.png"  style="width:14px;"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="color:#3485a4;text-decoration:none;font-size:12px;" href="employee_all.php">Employee Attendance</a></td>
                                </tr>
                                <?php 
								}
								/* End of Menu for Employee Attendance All */
								?>
                                <tr>
                                	<td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='accounting.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='accounting.php'">Store</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showadmindaily();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe3();HideMe();showadmindaily();" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Daily Schedule</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none" id="divdailymenu">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="technicallog.php" style="color:#3485a4;text-decoration:none;">Daily Sched</a></td>
                                            </tr>
                                            
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flyingrecord.php" style="color:#3485a4;text-decoration:none;" target="_blank">Daily Flying Record</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="technicallog.php?picstud=1" style="color:#3485a4;text-decoration:none;">PIC Flight Sched</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="technicallog.php?pending=1" style="color:#3485a4;text-decoration:none;">Pending Flight Sched</a></td>
                                            </tr>
                                            
                                           <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="addins.php" style="color:#3485a4;text-decoration:none;">Add New Instructor</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr> 
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='technicallog.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='technicallog.php'">Technical Log</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10">
                                    	<!--<img src="image/folder.png"  style="width:14px;" onclick="HideMe();showquestion();" style="cursor:pointer;">-->
                                        <?php //if($questionid == ""){?>
                                        <a href="loginquestion.php?source=1" class="lbOn" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;"><img src="image/folder.png"  style="width:14px;" style="cursor:pointer;"></a>
                                        <?php //} else {?>
                                        	<!--<img src="image/folder.png"  style="width:14px;" onclick="HideMe();showquestion();" style="cursor:pointer;">-->
                                        <?php //} ?>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                    <?php //if($questionid == ""){?>
                                        <a href="loginquestion.php?source=1" class="lbOn" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Question Bank</a>
                                        <?php // } else {?>
                                        	<!--<a onclick="HideMe3();HideMe();showquestion();" style="cursor:pointer;font-size:12px;">Question Bank</a>-->
                                        <?php //} ?>
                                    
                                    	<!--<a onclick="HideMe();showquestion();" style="cursor:pointer;font-size:12px;">Question Bank</a>-->
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px;"></td>
                                    <td class="nopadd" style="padding:0px;">
                                    <div id="divquestion" style="display:none;">
                                    	<table>
                                        	<?php if($stageandchapter == "1"){?>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="stagecreator.php" style="text-decoration:none;color:#3485a4;">Create Stages</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="addchapter.php" style="text-decoration:none;color:#3485a4;">Add Chapter</a></td>
                                            </tr>
                                            <?php } if($internal == "1" || $external == "1"){ ?>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="addquestion.php" style="text-decoration:none;color:#3485a4;">Add Question</a></td>
                                            </tr>
                                            <?php } if($stageandchapter == "1"){?>
                                           <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="schedule2.php" style="text-decoration:none;color:#3485a4;">Add Schedule</a></td>
                                            </tr>
                                            <?php } if($addinguser == "1"){?>
                                           <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="questionusers.php" style="text-decoration:none;color:#3485a4;">Add User</a></td>
                                            </tr>
                                            <?php } ?>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();show_gs_tki_report();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe3();HideMe();show_gs_tki_report();" style="cursor:pointer;font-size:12px;">TKI Commitment Reports</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div  id="div_gs_tki_report" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="tki_daily_hrs.php" target="_blank">Daily Commitment</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="tki_wkly_hrs.php">Weekly Commitment</a></td>
                                            </tr>
                                            
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="tki_annual_hrs.php" style="color:#3485a4;text-decoration:none;" target="_blank">Annual Commitment</a></td>
                                            </tr>
                                       	</table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showdaily();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe3();HideMe();showdaily();" style="cursor:pointer;font-size:12px;">Reports</a>
                                    </td>
                                </tr>
                                 <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div  id="divdaily" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flight_course_flow_report.php" style="color:#3485a4;text-decoration:none;" target="_blank">Flight Course Flow Report</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="dailyflyingplanningreport.php" style="color:#3485a4;text-decoration:none;">Planning & Achivement Report</a></td>
                                            </tr>
                                            
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flyingrecord.php" style="color:#3485a4;text-decoration:none;" target="_blank">Daily Record</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="instructorsreport.php" style="color:#3485a4;text-decoration:none;" target="_blank">Instructors Report</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd">
                                                	<!--a href="safetyreport1.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 1</a-->
                                                    <a href="aftermission_inside.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 1</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport2.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 2</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport1view.php" style="color:#3485a4;text-decoration:none;">View Flight Safety Report</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="view_aftermission_report.php?report_type=safety report" style="color:#3485a4;text-decoration:none;">View After Mission/Incident/Accident Report</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport2view.php" style="color:#3485a4;text-decoration:none;">View Share Your Experience</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flightsperday.php" style="color:#3485a4;text-decoration:none;">Flight Hours</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flight_student_attendance_report_v2.php" style="color:#3485a4;text-decoration:none;">Student Daily Report Sheet</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report2">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showdaily();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe3();HideMe();showsfoadmin();" style="cursor:pointer;font-size:12px;">Flight Safety Reports</a>
                                    </td>
                                </tr>
                                 <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div  id="divsfoadmin" style="display:none;">
                                    	<table>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd">
                                                	<!--a href="safetyreport1.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 1</a-->
                                                    <a href="aftermission_inside.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 1</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport2.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 2</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport1view.php" style="color:#3485a4;text-decoration:none;">View Flight Safety Report 1</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="view_aftermission_report.php?report_type=safety report" style="color:#3485a4;text-decoration:none;">View After Mission/Incident/Accident Report</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport2view.php" style="color:#3485a4;text-decoration:none;">View Share Your Experience</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showrequest();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe3();HideMe();showrequest();" style="cursor:pointer;font-size:12px;">Request Form</a>
                                    </td>
                                </tr>
                                 <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div id="divrequestform" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="passportreq.php" style="color:#3485a4;text-decoration:none;">Request for passport</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="passportreqapprovagml.php" style="color:#3485a4;text-decoration:none;">Passport Request Approval</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="leavereq.php" style="color:#3485a4;text-decoration:none;">Request for Leave</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="leavereqgm.php" style="color:#3485a4;text-decoration:none;" target="_blank">Leave Request Approval</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><a style="cursor:pointer;font-size:12px;text-decoration:none" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex; ?>&username=<?php echo $userusername; ?>&password=<?php echo $userpassword; ?>&userdecided=1" class="lbOn"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showrequest();" style="cursor:pointer;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex; ?>&username=<?php echo $userusername; ?>&password=<?php echo $userpassword; ?>&userdecided=1" class="lbOn">Change Password</a>
                                    </td>
                                </tr>
                               <!--tr>
                                	<td class="nopadd" width="10" id="reqadmin"><a style="cursor:pointer;font-size:12px;text-decoration:none" href="studentprogress_new.php"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showrequest();" style="cursor:pointer;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="studentprogress_new.php">SPMS</a>
                                    </td>
                                </tr-->
                                <tr>
                                	<td class="nopadd" width="10" id="marketing">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideAdministrator();ShowMarketing();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideAdministrator();ShowMarketing();" style="cursor:pointer;font-size:12px;">Marketing</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div id="divmarketing" style="display:none;">
                                    	<table>
                                        	<!--tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="add_info.php" style="color:#3485a4;text-decoration:none;">Add Guess</a></td>
                                            </tr-->
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="view_guess.php" style="color:#3485a4;text-decoration:none;">View Guess</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <?php if($checkndex == 3915 || $checkndex == 159 || $checkndex == 3945 || $checkndex == 28){?>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showadmindaily();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe3();HideMe();showsms();" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">SMS & EMAIL Sender</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divsms">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="marketing_sms.php" style="color:#3485a4;text-decoration:none;">Others</a></td>
                                            </tr>
											<?php if($checkndex == 3915 || $checkndex == 159){?>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="marketingedge_sms.php" style="color:#3485a4;text-decoration:none;">Edge SMS Campaign</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="externalexaminee_sms.php" style="color:#3485a4;text-decoration:none;">External Examinees</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="elpexaminee_sms.php" style="color:#3485a4;text-decoration:none;">ELP Examinees</a></td>
                                            </tr>
                                            <?php }?>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="staff_sms.php" style="color:#3485a4;text-decoration:none;">Administration</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_sms.php" style="color:#3485a4;text-decoration:none;" target="_blank">Students</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="instructor_sms.php" style="color:#3485a4;text-decoration:none;">Instructors</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <?php }?>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='check_security_expiry2.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='check_security_expiry2.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Expired Security</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='elp.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='elp.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">ELP</a>
                                    </td>
                                </tr> 
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='view_pending_task.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='view_pending_task.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Pending Task</a>
                                    </td>
                                </tr> 
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='reporting_system.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='reporting_system.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Reporting System</a>
                                    </td>
                                </tr>
                              <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='view_zone.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='view_zone.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">New Dawn Zone Status</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='course_schedule.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='course_schedule.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Course Schedule</a>
                                    </td>
                                </tr> 
                                <?php if($checkndex == 62 || $checkndex == 113 || $checkndex == 28)
								{?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='complain_sheet2.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='complain_sheet2.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Complain Sheet</a>
                                    </td>
                                </tr>
                                <?php } 
								/* Start of Menu for directory */
								if($checkndex == 62 || $checkndex == 3915 || $checkndex == 159 || $checkndex == 1  || $checkndex == 3912 || $checkndex == 3997 || $checkndex == 4110 || $checkndex == 4111)
								{?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='directory2.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='directory2.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Contact Directory</a>
                                    </td>
                                </tr>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='termsconditions.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='termsconditions.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Terms & Conditions</a>
                                    </td>
                                </tr>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='check_techlog_history.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='check_techlog_history.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Check Techlog Details & History</a>
                                    </td>
                                </tr>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='flight_schedule_sms.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='flight_schedule_sms.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Check Flight Schedule - SMS</a>
                                    </td>
                                </tr>
                                <?php 
								/* End of Menu for directory */
								}
								/* Start of Menu for procurement */
								if($checkndex == 159 || $checkndex == 3915 || $checkndex == 138 || $checkndex == 1 || $checkndex == 190 || $checkndex == 3984)
								{?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='procurement.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='procurement.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Procurement</a>
                                    </td>
                                </tr>
                                <?php 
								/* End of Menu for procurement */
								}/* Start of Menu for procurement */
								if($checkndex == 159 || $checkndex == 138 || $checkndex == 3915 || $checkndex == 190)
								{?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='faa_requisition_planning_pending.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='faa_requisition_planning_pending.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Requisition</a>
                                    </td>
                                </tr>
                                <?php 
								/* End of Menu for procurement */
								}
                                /* Start of Menu for harassment */
								if($checkndex == 159 || $checkndex == 3915 || $checkndex == 28)
								{?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='harassment_menu.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='harassment_menu.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Harassment Report</a>
                                    </td>
                                </tr>
                                <?php 
								}
								/* End of Menu for harassment */
                                /* Start of Menu for Aircraft Status */
								if($checkndex == 159 || $checkndex == 3915 || $checkndex == 190){?>
								 <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='aircrafthours.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='aircrafthours.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Aircraft Status</a></td>
                                </tr> 
                                <?php 
								}  
								/* End of Menu for Aircraft Status */
								/* Start of Menu for Authorization */
								if($checkndex == 159 || $checkndex == 3915 || $checkndex == 3997 || $checkndex == 3984){?>
								<tr>
									<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='authorization_code.php'" style="cursor:pointer;"></td>
									<td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='authorization_code.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Quality Authorization</a></td>
								</tr>
								<?php }
								/* End of Menu for Authorization */
								/* Start of Menu for who's online */
								if($checkndex == 3915 || $checkndex == 159 || $checkndex == 3997 || $checkndex == 4110 || $checkndex == 4111){?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='whosonline.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='whosonline.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Online Users</a>
                                    </td>
                                </tr>
                                <?php 
								/* End of Menu for who's online */?>
								<?php 
								/* Start of Menu for Certificate Template */?>
								<tr>
									<td class="nopadd" width="10">
										<img src="image/folder.png"  style="width:14px;" onclick="location.href='certificate_template.php'" style="cursor:pointer;">
									</td>
									<td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
										<a  onclick="location.href='certificate_template.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Certificate Template</a>
									</td>
								</tr>
								<?php 
								/* End of Menu for Certificate Template */
								/* Start of Menu for Student Pilot Authorization List */?>
								<tr>
									<td class="nopadd" width="10">
										<img src="image/folder.png"  style="width:14px;" onclick="location.href='spa_list.php'" style="cursor:pointer;">
									</td>
									<td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
										<a  onclick="location.href='spa_list.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Student Pilot Authorization List</a>
									</td>
								</tr>
								<?php 
								/* End of Menu for Student Pilot Authorization List */
								}?>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='skilltest_recommendation.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='skilltest_recommendation.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Skill Test Recommendation Status</a>
                                    </td>
                                </tr>
                                <?php
								/* Start of Menu for FI REVENUE (Viewing for Jeza, Tyron, Dan, & Capt. Yahya) */
								if($checkndex == 3915 || $checkndex == 159 || $checkndex == 3997 || $checkndex == 28)
								{
								?>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  href="fi_hrs_revenue.php"  style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">FI Revenue Hrs</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  href="fi_hrs_revenue_new.php"  style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">FI Revenue Hrs - New Format</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  href="flight_training_incomehrs.php"  style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Flight Training Income Hours</a>
                                    </td>
                                </tr>
								<?php 
								}
								/* End of Menu for FI REVENUE */
								?>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideMeAccounts();ShowReceiptLogs();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideAdministrator();ShowReceiptLogs();" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Receipt Logs</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px;"></td>
                                    <td class="nopadd" style="padding:0px;">
                                    <div id="divreceiptreport" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="receipt_logs.php?receipt_type=internal" style="color:#3485a4;text-decoration:none;">Internal Students</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="receipt_logs.php?receipt_type=external" style="color:#3485a4;text-decoration:none;">External Examinee</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="receipt_logs.php?receipt_type=elp" style="color:#3485a4;text-decoration:none;">ELP Test</a></td>
                                            </tr>
                                   		</table>
                                   	</div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='credit_card_logs.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Credit Card Logs</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a  onclick="HideAdministrator();ShowOnAccount();" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;"><img src="image/folder.png"  style="width:14px;" onclick="HideMeAccounts();ShowOnAccount();" style="cursor:pointer;"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="HideAdministrator();ShowOnAccount();" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">On Account Report</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px;"></td>
                                    <td class="nopadd" style="padding:0px;">
                                    <div id="divonaccountreport" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="onaccountreport.php?report_type=ee" style="color:#3485a4;text-decoration:none;">External Examinee</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="onaccountreport.php?report_type=elp" style="color:#3485a4;text-decoration:none;">ELP Test</a></td>
                                            </tr>
                                   		</table>
                                   	</div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a  onclick="HideAdministrator();ShowOnBlocked();" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;"><img src="image/folder.png"  style="width:14px;" onclick="HideAdministrator();ShowOnBlocked();" style="cursor:pointer;"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="HideAdministrator();ShowOnBlocked();" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Blocked Students</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px;"></td>
                                    <td class="nopadd" style="padding:0px;">
                                    <div id="divonblocked" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="studentfullyblocklist.php" style="color:#3485a4;text-decoration:none;">Fully Blocked - Current Students</a></td>
                                            </tr>
                                   		</table>
                                   	</div>
                                    </td>
                                </tr>
                                <?php if($auditees_session > 0 || $lead_auditor_session > 0 || $qam > 0){?>
                               	<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='quality_audit.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='quality_audit.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Quality Audit</a></td>
                                </tr>
                                <?php } ?> 
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><a style="cursor:pointer;font-size:12px;text-decoration:none" href="classroom_issues.php"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();" style="cursor:pointer;"></a></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="classroom_issues.php">Classroom Issue</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><a style="cursor:pointer;font-size:12px;text-decoration:none" href="admin_addstudent_new_course.php"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();" style="cursor:pointer;"></a></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="admin_addstudent_new_course.php">Add New Course To Student</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><a style="cursor:pointer;font-size:12px;text-decoration:none" href="airport_items.php"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();" style="cursor:pointer;"></a></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="airport_items.php">Airport Items</a></td>
                                </tr>
                                <?php if($checkndex == 3915 || $checkndex == 159){?>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  href="sentsms_activities.php"  style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">SMS History Logs</a></td>
                                </tr>
                                <?php }?>
                            </table>
                    </div>
                   <?php } if($dept == "1"){?>
               		<div style="width:20%;height:400px;border-right:solid 1px #8dcae3;">
                        <table>
                            <tr>
                                <td class="nopadd" width="10"><a onclick="HideMe2();showcourse();" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;"><img src="image/folder.png"  style="width:14px;" style="cursor:pointer;"></a></td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe2();showcourse();" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">My Record</a></td>
                            </tr>
                            <tr>
                                <td class="nopadd" style="padding:0px;"></td>
                                <td class="nopadd" style="padding:0px;">
                                <div id="divcourse" style="display:none;">
                                <?php 
                                $checkstatus = mysql_query("SELECT ndex,fldstatus,fldcourse FROM tblstudents WHERE flduserid='$checkndex' AND fldstatus='0'",$conn);
                                while($datacheckstatus = mysql_fetch_array($checkstatus))
                                {
                                    $ndex = $datacheckstatus['ndex'];
                                    $currentstatus = $datacheckstatus['fldstatus'];
                                    $coursecurrent = $datacheckstatus['fldcourse'];
                                    $currentcoursename = mysql_query("SELECT fldcourse FROM tblcourse WHERE ndex='$coursecurrent'",$conn);
                                    while($datacoursenamecurrent = mysql_fetch_array($currentcoursename)){
                                        $coursecurrentname = $datacoursenamecurrent['fldcourse'];
                                    }
                                    $ahrefcurrent = '<a href="studview_new.php?ndex='.$ndex.'&current=1" style="color:#3485a4;text-decoration:none;">'.$coursecurrentname.' (Current)</a>';	
                                    $showcurrent.='<tr><td class="nopadd"><img src="image/smallarrow.png"></td><td class="nopadd">'.$ahrefcurrent.'</td></tr>';
                                }
                                
                                $checkincomplete = mysql_num_rows(mysql_query("SELECT fldstatus FROM tblstudentsincomplete WHERE flduserid='$checkndex'",$conn));
                                if($checkincomplete != '0'){
                                    $checkcourseincomplete = mysql_query("SELECT fldstatus,fldcourse FROM tblstudentsincomplete WHERE flduserid='$checkndex'",$conn);
                                    while($datacourseincomplete = mysql_fetch_array($checkcourseincomplete)){
                                        $courseincomplete = $datacourseincomplete['fldcourse'];
                                        $incompletestatus = $datacourseincomplete['fldstatus'];
                                        $incompletecoursename = mysql_query("SELECT fldcourse FROM tblcourse WHERE ndex='$courseincomplete'",$conn);
                                        while($datacoursenameinc = mysql_fetch_array($incompletecoursename)){
                                            $courseincname = $datacoursenameinc['fldcourse'];
                                        }
                                        if($incompletestatus == "0"){
                                            $ahrefincomplete = '<a href="incompletestudview.php?ndex='.$ndex.'&pending=1" style="color:#3485a4;text-decoration:none;">'.$courseincname.' (Pending)</a>';
                                        }else{
                                            $ahrefincomplete = '<a href="incompletestudview.php?ndex='.$ndex.'&incomplete=1" style="color:#3485a4;text-decoration:none;">'.$courseincname.' (Unaccomplished)</a>';
                                        }
                                        $showincomplete.='<tr><td class="nopadd"><img src="image/smallarrow.png"></td><td class="nopadd">'.$ahrefincomplete.'</td></tr>';	
                                    }
                                }
                                
                                $checkcomplete = mysql_query("SELECT ndex,fldcourse FROM tblstudentscomplete WHERE flduserid='$checkndex'",$conn);
                                while($datacomplete = mysql_fetch_array($checkcomplete)){
                                    $coursecomplete = $datacomplete['fldcourse'];
                                    $completendex = $datacomplete['ndex'];
                                    $completecoursename = mysql_query("SELECT fldcourse FROM tblcourse WHERE ndex='$coursecomplete'",$conn);
                                    while($datacoursenamecomplete = mysql_fetch_array($completecoursename)){
                                    $coursecompletename = $datacoursenamecomplete['fldcourse'];
                                    }
                                    $ahrefcomplete ='<a href="studviewstud.php?ndex='.$ndex.'&completed=1&completendex='.$completendex.'" style="color:#3485a4;text-decoration:none;">'.$coursecompletename.' (Accomplished)</a>';
                                    $showcomplete.='<tr><td class="nopadd"><img src="image/smallarrow.png"></td><td class="nopadd">'.$ahrefcomplete.'</td></tr>';
                                }
                                ?>
                                    <table>
                                        <?php echo $showcurrent.$showincomplete.$showcomplete;?>                                          
                                    </table>
                                    </div>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='flight_ops_policy2.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='flight_ops_policy2.php'">Flight Operation Policy</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='technicallog.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='technicallog.php'">Daily Schedule</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='stud_quiz.php?view=4&studuserid=<?php echo $checkndex;?>'"><img src="image/folder.png" style="width:14px;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='stud_quiz.php?view=4&studuserid=<?php echo $checkndex;?>'">Student Quiz</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='stud_feedback.php?view=1&studuserid=<?php echo $checkndex;?>'"><img src="image/folder.png" style="width:14px;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='stud_feedback.php?view=1&studuserid=<?php echo $checkndex;?>'">Student Feedback</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="HideMe2();showexam();"><img src="image/folder.png"  style="width:14px;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="HideMe2();showexam();">Exam</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" style="padding:0px;">
                                    
                                </td>
                                <td class="nopadd" style="padding:0px;">
                                <div  id="divexam" style="display:none;">
                                    <?php /*********encryption*************************/
                                    $l_secure_query = 'checkndex='.$checkndex.'&dept=1&comp_name='.$comp_name;  
                                    $l_encrypted = doEncrypt($l_secure_query); 
                                    /**********************************************/
                                    ?>
                                    <table>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="<?php echo $address_link; ?>verify.php?<?php echo $l_encrypted; ?>" style="color:#3485a4;text-decoration:none;">Schedules</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="<?php echo $address_link; ?>verify.php?<?php echo $l_encrypted; ?>" style="color:#3485a4;text-decoration:none;">Results</a></td>
                                        </tr>
                                       
                                    </table>
                                    </div>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='request.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='request.php'">Sched Request</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='viewtechlog.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                    <a  style="cursor:pointer;font-size:12px;" onclick="location.href='viewtechlog.php'">Check Tech Log</a>
                                </td>
                           </tr>     
                           <tr>
                                <td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='changepasswordstud.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                </td>     
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                    <a  style="cursor:pointer;font-size:12px;" onclick="location.href='changepasswordstud.php'">Change Password</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10" id="report">
                                    <img src="image/folder.png"  style="width:14px;" onclick="HideMe2();showrequest();'" style="cursor:pointer;"></td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe2();showrequest();" style="cursor:pointer;font-size:12px;">Request Form</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" style="padding:0px"></td>
                                <td class="nopadd" style="padding:0px">
                                <div id="divrequestform" style="display:none;">
                                    <table>
                                        
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="passportreq.php" style="color:#3485a4;text-decoration:none;">Request for passport</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="studentleavereq.php" style="color:#3485a4;text-decoration:none;">Request for leave</a></td>
                                        </tr>
                                         <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="add_new_course.php" style="color:#3485a4;text-decoration:none;" target="_blank">Apply for new course</a></td>
                                        </tr>
                                         <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="elp_application.php" style="color:#3485a4;text-decoration:none;" target="_blank">Apply ELP</a></td>
                                        </tr>
                                         <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="security_pass.php?lang=1" style="color:#3485a4;text-decoration:none;" target="_blank">Security Pass Engish</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="security_pass.php?lang=2" style="color:#3485a4;text-decoration:none;" target="_blank">Security Pass Arabic (arabic passport holder)</a></td>
                                        </tr>
                                    </table>
                                    </div>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10" id="reportstud">
                                    <img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showdaily();" style="cursor:pointer;"></td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe2();showsfostud();" style="cursor:pointer;font-size:12px;">Flight Safety Reports</a>
                                </td>
                            </tr>
                             <tr>
                                <td class="nopadd" style="padding:0px"></td>
                                <td class="nopadd" style="padding:0px">
                                <div  id="divsfostud" style="display:none;">
                                    <table>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd">
                                                <!--a href="safetyreport1.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 1</a-->
                                                <a href="aftermission_inside.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 1</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="safetyreport2.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 2</a></td>
                                        </tr>
                                    </table>
                                    </div>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10" id="report"><img src="image/folder.png"  style="width:14px;" style="cursor:pointer;"></td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="new_message_list.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Messages</a></td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='course_schedule.php'" style="cursor:pointer;"></td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='course_schedule.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Course Schedule</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='record_of_emergency_drills_confirmation.php?ndex=<?php echo $ndex; ?>'" style="cursor:pointer;"></td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='record_of_emergency_drills_confirmation.php?ndex=<?php echo $ndex; ?>'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Emergency Drills Confirmation</a>
                                </td>
                            </tr>
                            <!--tr>
                                <td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='student_critique.php'" style="cursor:pointer;"></td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='student_critique.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Ground School Course Critique</a>
                                </td>
                            </tr-->
                            <tr>
                                <td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='student_critique.php'" style="cursor:pointer;"></td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='pending_debrief_signature.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Debrief Sheets Required Signature</a>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10" id="reqadmin"><a style="cursor:pointer;font-size:12px;text-decoration:none" href="classroom_issues.php"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();" style="cursor:pointer;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;font-weight:bold;"><a style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="classroom_issues.php">Classroom Issue</a>
                                </td>
                            </tr>
                         </table>
                    </div>
                    <?php } if($dept == "1i" && $checkndex != 5696 && $checkndex != 8745 && $checkndex != 8746 && $checkndex != 8790){?>
               		<div style="width:20%;height:400px;border-right:solid 1px #8dcae3;">
                        	<table>
                                <!--tr>
                                <td class="nopadd" width="10">
                                <a  style="cursor:pointer;font-size:12px;" onclick="location.href='otherusers_view.php?<?php echo $l_encrypted; ?>'"><img src="image/folder.png"  style="width:14px;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                <a  style="cursor:pointer;font-size:12px;" onclick="location.href='otherusers_view.php?<?php echo $l_encrypted; ?>'">My Profile</a>
                                </td>
                                </tr-->
                                <?php if($flightins == "flightinstructor" && $checkndex != 1586){?>
                            	 <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" href="employee_file.php?ndex=<?php echo $checkndex; ?>&sel_dept=6"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;" href="employee_file.php?ndex=<?php echo $checkndex; ?>&sel_dept=6">My HR Profile</a>
                                    </td>
                                </tr>
                                <?php } ?>
                                <?php if($flightins == "" && $groundins == "groundinstructor"){?>
                            	 <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" href="employee_file.php?ndex=<?php echo $checkndex; ?>&sel_dept=7"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;" href="employee_file.php?ndex=<?php echo $checkndex; ?>&sel_dept=7">My HR Profile</a>
                                    </td>
                                </tr>
                                <?php } ?>
								<?php /* Start of Menu for HR Employee File for Capt. Jose*/
                                if($checkndex == 1586)
								{?>
                            	<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideAdministrator();showotherhremp();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideAdministrator();showotherhremp();" style="cursor:pointer;font-size:12px;">HR Employee File</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divotherhremp">
                                    	<table>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=11" style="color:#3485a4;text-decoration:none;">Management</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=1" style="color:#3485a4;text-decoration:none;">Administration</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=2" style="color:#3485a4;text-decoration:none;">Accounts</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=10" style="color:#3485a4;text-decoration:none;">Marketing</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=3" style="color:#3485a4;text-decoration:none;">Aircraft Maintenance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=5" style="color:#3485a4;text-decoration:none;">Maintenance Engineering Training</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=12" style="color:#3485a4;text-decoration:none;">Flight Operations</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=6" style="color:#3485a4;text-decoration:none;">Flight Training</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=14" style="color:#3485a4;text-decoration:none;">Flight Training (A) Flight</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=13" style="color:#3485a4;text-decoration:none;">Flight Training (H) Flight</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=7" style="color:#3485a4;text-decoration:none;">Flight Training Ground School</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=8" style="color:#3485a4;text-decoration:none;">Safety And Quality Assurance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=9" style="color:#3485a4;text-decoration:none;">IT</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=4" style="color:#3485a4;text-decoration:none;">Support Staffs</a></td>
                                            </tr> 
                                       	</table>
                                       </div>
                                    </td>
                                </tr>
                                <?php 
								}
								/* End of Menu for HR Employee File (Capt. Jose) */
                                ?>
                                <?php /* Start of Menu for HR Employee File for CTKI*/
								if($chiefins == 1  && $groundins == "groundinstructor" && $checkndex != 1586 && $checkndex != 7253){?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='other_users_hr.php?sel_dept=7'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="other_users_hr.php?sel_dept=7" style="cursor:pointer;color:#3485a4;font-size:12px;text-decoration:none;">HR Employee File - TKI</a>
                                    </td>
                                </tr>
                                <?php 
								}/* End of Menu for HR Employee File for CTKI */?>
                                <?php /* Start of Menu for HR Employee File for HOT & CFI*/
								if((($chiefins == 1  && $flightins != "") || $hot == 1)  && $checkndex != 1586){?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="showotherhremp();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="showotherhremp();" style="cursor:pointer;font-size:12px;">HR Employee File</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divotherhremp">
                                    	<table>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=6" style="color:#3485a4;text-decoration:none;">Flight Training</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=14" style="color:#3485a4;text-decoration:none;">Flight Training (A) Flight</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=13" style="color:#3485a4;text-decoration:none;">Flight Training (H) Flight</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="other_users_hr.php?sel_dept=7" style="color:#3485a4;text-decoration:none;">Flight Training Ground School</a></td>
                                            </tr>
                                       	</table>
                                       </div>
                                    </td>
                                </tr>
                                <?php 
								}/* End of Menu for HR Employee File for CTKI */?>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideMe();showstudmenu();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe();showstudmenu();" style="cursor:pointer;font-size:12px;">Student</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divstudmenu">
                                    	<table>
                               
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="allselect.php" style="color:#3485a4;text-decoration:none;">All Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="studselect.php" style="color:#3485a4;text-decoration:none;">Current Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="pendingstudent.php" style="color:#3485a4;text-decoration:none;">Pending Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="incompleteselect.php" style="color:#3485a4;text-decoration:none;">Unaccomplished Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="accomplishselect.php" style="color:#3485a4;text-decoration:none;">Accomplished Student</a></td>
                                            </tr>
											<?php if($flightins == "" && $groundins == "groundinstructor"){?>
                                            <tr>
                                                <td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd">
                                                    <a style="color:#3485a4;text-decoration:none;" onclick="location.href='stud_quiz.php'">Student Quiz</a></td>
                                            </tr>
                                            <?php } ?>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="stud_feedback.php?view=3" style="color:#3485a4;text-decoration:none;">Student Feedback</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideMe();showinsmenu();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='finsview.php?myuserid=<?php echo $checkndex; ?>'" style="cursor:pointer;font-size:12px;">My Record</a>
                                    </td>
                                </tr>
                                 <tr>
                                	<td class="nopadd" style="padding:0px;"></td>
                                    <td class="nopadd" style="padding:0px;">
                                    <div style="display:none;" id="divinsmenu">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="insselect.php" style="color:#3485a4;text-decoration:none;">Current Instructor</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="resignedselect.php" style="color:#3485a4;text-decoration:none;" target="_blank">Resigned Instructor</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="addins.php" style="color:#3485a4;text-decoration:none;">Add New Instructor</a></td>
                                            </tr>
                                             <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flyingrecord_ins.php" style="color:#3485a4;text-decoration:none;">Pilot's Daily Flying Record</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideMe();showdaily();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="HideMe();HideMeIns();ShowDailyIns();">Daily Schedule</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div id="divdailyins" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a onclick="location.href='technicallog.php'" style="color:#3485a4;text-decoration:none;cursor:pointer;">View Daily Sched.</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a onclick="location.href='technicallogedit.php'" style="color:#3485a4;text-decoration:none;cursor:pointer;">Edit Tech. Log Hrs</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='viewtechlog.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                        <a  style="cursor:pointer;font-size:12px;" onclick="location.href='viewtechlog.php'">Check Tech Log</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='request.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='request.php'">Sched Request</a>
                                    </td>
                                </tr>
                                
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='technicallog.php?picstud=1'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='technicallog.php?picstud=1'">PIC Student</a>
                                    </td>
                                </tr>
                               <tr>
                                	<td class="nopadd" width="10">
                                        <a href="loginquestion.php?source=1" class="lbOn" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                        <?php // if($questionid == ""){?>
                                        <a href="loginquestion.php?source=1" class="lbOn" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Question Bank</a>
                                        <?php // } else {?>
                                        	<!--<a onclick="HideMe();showquestion();" style="cursor:pointer;font-size:12px;">Question Bank</a>-->
                                        <?php // } ?>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='changepassword.php'"><img src="image/folder.png"  style="width:14px;"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='changepassword.php'">Change Password</a></td>
                                </tr>
                                <?php if($chiefins == "1"){?>
                                <tr>
                                	<td class="nopadd" width="10" id="report">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideMeChief();showdaily();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMeChief();showdaily();" style="cursor:pointer;font-size:12px;">Reports</a>
                                    </td>
                                </tr>
                                 <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div  id="divdaily" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flight_course_flow_report.php" style="color:#3485a4;text-decoration:none;" target="_blank">Flight Course Flow Report</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="dailyflyingplanningreport.php" style="color:#3485a4;text-decoration:none;">Planning & Achievement Report</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flightsperday.php" style="color:#3485a4;text-decoration:none;">Flight Hours</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flyingrecord.php" style="color:#3485a4;text-decoration:none;" target="_blank">Daily Record</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="instructorsreport.php" style="color:#3485a4;text-decoration:none;" target="_blank">Instructors Report</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><!--a href="safetyreport1.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 1</a-->
                                                <a href="aftermission_inside.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 1</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <!--tr>
                                	<td class="nopadd" width="10" id="report"><img src="image/folder.png"  style="width:14px;cursor:pointer;" onclick="location.href='dutytimefi_new.php'"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='dutytimefi_new.php'" style="cursor:pointer;font-size:12px;">F.I. Duty Time</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report"><img src="image/folder.png"  style="width:14px;cursor:pointer;" onclick="location.href='studentprogress_new.php'"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='studentprogress_new.php'" style="cursor:pointer;font-size:12px;">SPMS</a></td>
                                </tr-->
                                <?php } 
								if($chiefins != "1"){ ?>
                                <!--tr>
                                	<td class="nopadd" width="10" id="report"><img src="image/folder.png"  style="width:14px;cursor:pointer;" onclick="location.href='studentprogress_new.php'"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='studentprogress_new.php'" style="cursor:pointer;font-size:12px;">SPMS</a></td>
                                </tr-->
                                <tr>
                                	<td class="nopadd" width="10" id="report"><img src="image/folder.png" style="width:14px;cursor:pointer;" onclick="HideMeChief();showdaily();"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMeChief();showdaily();" style="cursor:pointer;font-size:12px;">Reports</a></td>
                                </tr>
                                 <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div  id="divdaily" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="flight_course_flow_report.php" style="color:#3485a4;text-decoration:none;" target="_blank">Flight Course Flow Report</a></td>
                                            </tr>
                                        </table>
                                   	</div>
                                    </td>
                                </tr>             
                                <?php } ?>
                                <tr>
                                	<td class="nopadd" width="10" id="report"><a href="flight_student_attendance_report_v2.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none"><img src="image/folder.png"  style="width:14px;cursor:pointer"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="flight_student_attendance_report_v2.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none">Student Daily Report Sheet</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report"><img src="image/folder.png"  style="width:14px;cursor:pointer;" onclick="HideMe3();HideMe();show_gs_report();"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe();show_gs_report();" style="cursor:pointer;font-size:12px;">Student Theoretical Progress Report</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div  id="div_gs_report" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="gs_report.php" target="_blank">Examination Summary</a></td>
                                            </tr>
                                        	<!--tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="gs_report_per_student.php">Ground Record Per Student</a></td>
                                            </tr-->
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="studentprogress_report_gs.php" style="color:#3485a4;text-decoration:none;" target="_blank">Student Progress Report</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="gs_quizreport.php" target="_blank">Quizzes Summary</a></td>
                                            </tr>
                                       	</table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();show_gs_tki_report();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe();show_gs_tki_report();" style="cursor:pointer;font-size:12px;">TKI Commitment Reports</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div  id="div_gs_tki_report" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="tki_daily_hrs.php" target="_blank">Daily Commitment</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a style="color:#3485a4;text-decoration:none;" href="tki_wkly_hrs.php">Weekly Commitment</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="tki_annual_hrs.php" style="color:#3485a4;text-decoration:none;" target="_blank">Annual Commitment</a></td>
                                            </tr>
                                       	</table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="insreq"><img src="image/folder.png"  style="width:14px;" onclick="HideMe();showrequest();'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe();showrequest();" style="cursor:pointer;font-size:12px;">Request Form</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div id="divrequestform" style="display:none;">
                                    	<table>
                                        	 <?php if($chiefins == "1" || $hot == "1"){?>
                                             <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="queriedrequest.php" style="color:#3485a4;text-decoration:none;">Approval Request Ext. Duty Time</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="leavereq_general.php" style="color:#3485a4;text-decoration:none;" target="_blank">Leave Request Approval</a></td>
                                            </tr>
                                            <?php } ?>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="instructorrequestapproval.php" style="color:#3485a4;text-decoration:none;">Request Ext. Duty Time</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="passportreq.php" style="color:#3485a4;text-decoration:none;">Request for Passport</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="leavereq.php" style="color:#3485a4;text-decoration:none;">Request for Leave</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="insduty"><img src="image/folder.png" style="width:14px;" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="dutytimefi_new.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Flight Duty Time</a></td>
                                </tr>
                                <?php if($qam == "1"){?>
                                <tr>
                                	<td class="nopadd" width="10" id="insduty"><img src="image/folder.png" style="width:14px;" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="dutytimeadminsqlforallengrins.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">E.I. Duty Time</a></td>
                                </tr>
                                <?php } ?>
                                <tr>
                                	<td class="nopadd" width="10" id="report"><img src="image/folder.png"  style="width:14px;" onclick="HideMe();showsfo();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe();showsfo();" style="cursor:pointer;font-size:12px;">Flight Safety Report</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div id="divsfo" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><!--a href="safetyreport1.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 1</a-->
                                                <a href="aftermission_inside.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 1</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport2.php" style="color:#3485a4;text-decoration:none;">Add Flight Safety Report 2</a></td>
                                            </tr>
                                            <?php if($sfo == "1"){?>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport1view.php" style="color:#3485a4;text-decoration:none;">View Flight Safety Report 1</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="safetyreport2view.php" style="color:#3485a4;text-decoration:none;">View Flight Safety Report 2</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="view_aftermission_report.php?report_type=safety report" style="color:#3485a4;text-decoration:none;">View After Mission/Incident/Accident Report</a></td>
                                            </tr>
                                            <?php } ?>
                                        </table>
                                    </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report"><img src="image/folder.png"  style="width:14px;" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="new_message_list.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Messages</a></td>
                                </tr>
                                <?php if($chiefins == "1"){?>
                                 <tr>
                                	<td class="nopadd" width="10" id="report"><img src="image/folder.png"  style="width:14px;" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="add_instructions.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Broadcast Message</a></td>
                                </tr>
                                <?php 
								}
								if($hotins == "1"){?>
                                 <tr>
                                	<td class="nopadd" width="10" id="report"><img src="image/folder.png"  style="width:14px;" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="register_select.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Student Applicants</a></td>
                                </tr>
                                <?php } ?>
                                <tr>
                                	<td class="nopadd" width="10" id="recurrent_id"><img src="image/folder.png"  style="width:14px;" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMeIns();ShowRecurrent();" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Recurrent Exam</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div  id="divrecurrent" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd">
                                                <?php 
												$QueryExamRecurrent = mysql_query("SELECT ndex FROM tblexam_specification WHERE fldsubject ='recurrent' order by ndex desc limit 0,1",$conn);
												while($DataExamRecurrent = mysql_fetch_array($QueryExamRecurrent)){
													$Exam_Recurrent_ID = $DataExamRecurrent['ndex'];
												}
												?>
                                                	<a href="examstart_instructor.php?checkndex=<?php echo $checkndex; ?>&Exam_Recurrent_ID=<?php echo $Exam_Recurrent_ID; ?>" style="color:#3485a4;text-decoration:none;">Take Recurrent Exam</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="recurrent_exam_attempts.php?instructor_id=<?php echo $checkndex; ?>" style="color:#3485a4;text-decoration:none;">View Results</a></td>
                                            </tr>
                                            <?php if($hotins == "1" || $chiefins == "1"){?>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="recurrent_exam.php" style="color:#3485a4;text-decoration:none;">View Instructors Recurrency Status</a></td>
                                            </tr>
                                            <?php } ?>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="recurrent_id"><img src="image/folder.png"  style="width:14px;" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="pending_flight_plan.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Pending Flight Plan</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='elp.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='elp.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">ELP</a></td>
                                </tr> 
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='flightsperday.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='flightsperday.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Flight Hours</a></td>
                                </tr> 
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='aircrafthours.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='aircrafthours.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Aircraft Status</a></td>
                                </tr> 
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;cursor:pointer;" onclick="location.href='course_schedule.php'"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='course_schedule.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Course Schedule</a></td>
                                </tr> 
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png" style="width:14px;cursor:pointer;" onclick="location.href='reporting_system.php'"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='reporting_system.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Reporting System</a></td>
                                </tr>
								<?php 
								/*if($dept == "1i" && $chiefins == "0" && $flightins == "flightinstructor" && $groundins == "groundinstructor" && $hot == "1"){?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;cursor:pointer;" onclick="location.href='student_critique.php'"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='student_critique.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Student Critique</a></td>
                                </tr>
                                <?php 
								}
								if($dept == "1i" && $chiefins == "1" && ($flightins == "flightinstructor" || $groundins == "groundinstructor")){?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='student_critique.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='student_critique.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Student Critique</a>
                                    </td>
                                </tr>
                                <?php 
								}
                              	if($dept == "1i" && ($chiefins == "1" || $hot == "1") && ($flightins == "flightinstructor" || $groundins == "groundinstructor")){?>
								<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;cursor:pointer;" onclick="location.href='complain_sheet2.php'"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='complain_sheet2.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Complain Sheet</a></td>
                                </tr>
                                <?php } */?>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png" style="width:14px;cursor:pointer;" onclick="location.href='dutytime_students.php'"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='dutytime_students.php'" style="cursor:pointer;font-size:12px;">Attendance <font style="font-size:10px;font-weight:normal;font-style:italic;">(Flight Students)</font></a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideMe();showattendance();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMe();showattendance();" style="cursor:pointer;font-size:12px;">Attendance <font style="font-size:10px;font-weight:normal;font-style:italic;">(Theoretical Students)</font></a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divattendance">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance.php" style="color:#3485a4;text-decoration:none;">Create Attendance</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="actt_attendance.php" style="color:#3485a4;text-decoration:none;">Create Additional Type Tech Attendance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_view.php" style="color:#3485a4;text-decoration:none;">View Daily Attendance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_subjects.php" style="color:#3485a4;text-decoration:none;">View Subject Attendance</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="student_attendance_all.php" style="color:#3485a4;text-decoration:none;">View All Student Attendance</a></td>
                                            </tr>
                                        </table>
                                    </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='skilltest_recommendation.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='skilltest_recommendation.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Skill Test Recommendation Status</a></td>
                                </tr> 
                                <!--tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='atctestresults.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='atctestresults.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">ATC Test Results</a></td>
                                </tr-->
                                <?php if($hot == "1"){?> 
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='gs_completion_pending.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='gs_completion_pending.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Pending GS Completion </a></td>
                                </tr> 
                                <?php } 
								/* Start of Menu for Certificate Template */
								if($dept == "1i" && $checkndex == 52){
								?>
								<tr>
									<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='certificate_template.php'" style="cursor:pointer;"></td>
									<td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='certificate_template.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Certificate Template</a></td>
								</tr>
								<?php 
								/* End of Menu for Certificate Template */
								}
								if($chiefins == "1" || $hot == "1"){
                                /* Start of Menu for Student Pilot Authorization List */?>
                                <tr>
                                    <td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='spa_list.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='spa_list.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Student Pilot Authorization List</a></td>
                                </tr>
                                <?php 
                                /* End of Menu for Student Pilot Authorization List */
                                } if($auditees_session > 0 || $lead_auditor_session > 0 || $qam > 0){?>
                               	<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='quality_audit.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='quality_audit.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Quality Audit</a></td>
                                </tr>
                                <?php } ?>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><a style="cursor:pointer;font-size:12px;text-decoration:none" href="classroom_issues.php"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();" style="cursor:pointer;"></a></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="classroom_issues.php">Classroom Issue</a></td>
                                </tr>
                            </table>
                    </div>
					<?php } if($dept == "1i" && $checkndex == 8790){?>
               		<div style="width:20%;height:400px;border-right:solid 1px #8dcae3;">
                        	<table  width="280">
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideMe();showstudmenu();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="showstudmenu();" style="cursor:pointer;font-size:12px;">Student</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divstudmenu">
                                    	<table>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="studselect.php" style="color:#3485a4;text-decoration:none;">Current Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="accomplishselect.php" style="color:#3485a4;text-decoration:none;">Accomplished Student</a></td>
                                            </tr>
                                            <tr>
                                                <td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="stud_feedback.php?view=3" style="color:#3485a4;text-decoration:none;">Student Feedback</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="intructorslink">
                                    	<img src="image/folder.png"  style="width:14px;" onclick="HideSafety();showinsmenu();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="showinsmenu();" style="cursor:pointer;font-size:12px;">Instructor</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px;"></td>
                                    <td class="nopadd" style="padding:0px;">
                                    <div style="display:none;" id="divinsmenu">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="insselect.php" style="color:#3485a4;text-decoration:none;">Current Instructor</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="resignedselect.php" style="color:#3485a4;text-decoration:none;" target="_blank">Resigned Instructor</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='technicallog.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='technicallog.php'" style="color:#3485a4;text-decoration:none;cursor:pointer;">Daily Schedule</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='viewtechlog.php'"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                        <a  style="cursor:pointer;font-size:12px;" onclick="location.href='viewtechlog.php'">Check Tech Log</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="report"><img src="image/folder.png"  style="width:14px;cursor:pointer;" onclick="location.href='dutytimefi_new.php'"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='dutytimefi_new.php'" style="cursor:pointer;font-size:12px;">F.I. Duty Time</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png" style="width:14px;cursor:pointer;" onclick="location.href='dutytime_students.php'"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='dutytime_students.php'" style="cursor:pointer;font-size:12px;">Attendance <font style="font-size:10px;font-weight:normal;font-style:italic;">(Flight Students)</font></a></td>
                                </tr>
                            </table>
                    </div>
                    <?php } 
					if($dept == "Accounting"){?>
               		<div style="width:20%;height:800px;border-right:solid 1px #8dcae3;">
                        	<table width="280">
                                <!--tr>
                                <td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='otherusers_view.php?<?php echo $l_encrypted; ?>'"><img src="image/folder.png"  style="width:14px;"></a></td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='otherusers_view.php?<?php echo $l_encrypted; ?>'">My Profile</a></td>
                                <!--<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='procurement_approved.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='procurement_approve.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Procurements</a>
                                    </td>
                                </tr>>
                                </tr-->
                            	 <tr>
                                	<td class="nopadd" width="10"><a  style="cursor:pointer;font-size:12px;" href="employee_file.php?ndex=<?php echo $checkndex; ?>&sel_dept=2"><img src="image/folder.png"  style="width:14px;"></a>
                                    </td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;" href="employee_file.php?ndex=<?php echo $checkndex; ?>&sel_dept=2">My HR Profile</a>
                                    </td>
                                </tr>
								<?php /* Start of Menu for HR Employee File for Mr. Charles*/
								if($checkndex == 17){?>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='other_users_hr.php?sel_dept=2'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a href="other_users_hr.php?sel_dept=2" style="cursor:pointer;color:#3485a4;font-size:12px;text-decoration:none;">HR Employee File - Accounts</a>
                                    </td>
                                </tr>
                                <?php 
								}/* End of Menu for HR Employee File for Mr. Charles */?>
                                <?php if($checkndex != 4081){?>
                            	<tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideMe();showstudmenu();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMeAccounts();showstudmenu();" style="cursor:pointer;font-size:12px;">Student</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divstudmenu">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="studselect.php" style="color:#3485a4;text-decoration:none;">Current Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="pendingstudent.php" style="color:#3485a4;text-decoration:none;">Pending Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="incompleteselect.php" style="color:#3485a4;text-decoration:none;">Unaccomplished Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="accomplishselect.php" style="color:#3485a4;text-decoration:none;">Accomplished Student</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="course_schedule_summary.php" style="color:#3485a4;text-decoration:none;">Course Schedule Yearly Summary</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <?php } ?>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideMe();showprocurement();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMeAccounts();showprocurement();" style="cursor:pointer;font-size:12px;">Procurement</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px">
                                    </td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divprocurement">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="procurement_pending.php" style="color:#3485a4;text-decoration:none;">Pending Transaction</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="procurement_close.php" style="color:#3485a4;text-decoration:none;">Closed Transaction</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="procurement_cancel.php" style="color:#3485a4;text-decoration:none;">Cancelled Transaction</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <?php if($checkndex != 4081){?>
                                <!--tr>
                                	<td class="nopadd" width="10" id="reqadmin"><a style="cursor:pointer;font-size:12px;text-decoration:none" href="studentprogress_new.php"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;"></a></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="studentprogress_new.php">SPMS</a></td>
                                </tr-->
                                <?php } ?>
                                <tr>
                                	<td class="nopadd" width="10" id="intructorslink"><img src="image/folder.png"  style="width:14px;" onclick="HideMe();showinsmenu();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMeAccounts();showinsmenu();" style="cursor:pointer;font-size:12px;">Instructor</a></td>
                                </tr>
                                 <tr>
                                	<td class="nopadd" style="padding:0px"></td>
                                    <td class="nopadd" style="padding:0px">
                                    <div style="display:none;" id="divinsmenu">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="insselect.php" style="color:#3485a4;text-decoration:none;">Current Instructor</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="pilotstatus.php" style="color:#3485a4;text-decoration:none;" target="_blank">Pilot's Status</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="resignedselect.php" style="color:#3485a4;text-decoration:none;" target="_blank">Resigned Instructor</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                 <tr>
                                	<td class="nopadd" style="padding:0px;"></td>
                                    <td class="nopadd" style="padding:0px;">
                                    <div style="display:none;" id="divinsmenu">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="insselect.php" style="color:#3485a4;text-decoration:none;">Current Instructor</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="resignedselect.php" style="color:#3485a4;text-decoration:none;" target="_blank">Resigned Instructor</a></td>
                                            </tr>	
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="addins.php" style="color:#3485a4;text-decoration:none;">Add New Instructor</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='biometric_users.php'"><img src="image/folder.png"  style="width:14px;"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='biometric_users.php'">Other Staffs</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='student_attendance_all_with_date.php'"><img src="image/folder.png"  style="width:14px;"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='student_attendance_all_with_date.php'">Attendance</a></td>
                                </tr>
                                <?php if($checkndex != 4081){?>
                                <tr>
                                	<td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='examinees.php'"><img src="image/folder.png"  style="width:14px;"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='examinees.php'">Examinees</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='technicallog.php'"><img src="image/folder.png"  style="width:14px;"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='accounting.php'">Accounting</a></td>
                                </tr>
                                 <tr>
                                	<td class="nopadd" style="padding:0px;"></td>
                                    <td class="nopadd" style="padding:0px;">
                                    <div id="divquestion" style="display:none;">
                                    </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='aircraftreceiving.php'"><img src="image/folder.png"  style="width:14px;"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='aircraftreceiving.php'">Price Update</a></td>
                                </tr>
                                <?php } ?>
                                 <tr>
                                	<td class="nopadd" style="padding:0px;"></td>
                                    <td class="nopadd" style="padding:0px;">
                                    <div id="divquestion" style="display:none;">
                                    </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="HideMeAccounts();showrequest2();"><img src="image/folder.png"  style="width:14px;"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;"  onclick="HideMeAccounts();showrequest2();">Request Form</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px;"></td>
                                    <td class="nopadd" style="padding:0px;">
                                    <div id="divrequestform2" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="passportreq.php" style="color:#3485a4;text-decoration:none;">Request for passport</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="passportreqapproval.php" style="color:#3485a4;text-decoration:none;">Passport Request Approval</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="leavereq.php" style="color:#3485a4;text-decoration:none;">Request for Leave</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="leavereq_general.php" style="color:#3485a4;text-decoration:none;">Leave Request Approval</a></td>
                                            </tr>
                                        </table>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><a style="cursor:pointer;font-size:12px;text-decoration:none" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex; ?>&username=<?php echo $userusername; ?>&password=<?php echo $userpassword; ?>&userdecided=1" class="lbOn"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showrequest();" style="cursor:pointer;"></a></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex; ?>&username=<?php echo $userusername; ?>&password=<?php echo $userpassword; ?>&userdecided=1" class="lbOn">Change Password</a></td>        
                                </tr>
                                <?php if($checkndex != 4081){?>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showrequest();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a href="elp.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">ELP / Student Applicants</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showrequest();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a href="elp_paid.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">ELP Paid Examinees</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();showrequest();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a href="elp_completed.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">ELP Completed Exams</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><img src="image/folder.png"  style="width:14px;" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a href="exam_registration.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Applicants</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;" onclick="location.href='paid_examinees.php'"></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a href="paid_examinees.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">All Paid Examinees</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><img src="image/folder.png"  style="cursor:pointer;" onclick="location.href='lcategory_examinees_all.php'"></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;">
                                    	<a href="lcategory_examinees_all.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">L Category Paid Examinees</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;" onclick="location.href='paid_examinees_dubai.php'"></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a href="paid_examinees_dubai.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Dubai Examinees Completed Exam</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;" onclick="location.href='paid_examinees_dubai_all.php'"></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a href="paid_examinees_dubai_all.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Dubai All Paid Examinees</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin">
                                    	<img src="image/folder.png"  style="cursor:pointer;" onclick="location.href='paid_examinees_dubai_amended_all.php'">
                                    </td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;">
                                    	<a href="paid_examinees_dubai_amended_all.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Dubai Amended Booking Paid Examinees</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;" onclick="location.href='online_trx.php'"></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a href="online_trx.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Online Payment Transactions</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10" id="reqadmin"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;" onclick="location.href='refuel_logs_all.php'"></td>
                                    <td class="nopadd" style="font-size:14px;font-weight:bold;"><a href="refuel_logs_all.php" style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;">Refuel Logs</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="location.href='course_schedule.php'" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="location.href='course_schedule.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Course Schedule</a></td>
                                </tr>
                                <?php } ?>
                                <tr>
                                	<td class="nopadd" width="10"><a onclick="location.href='credit_card_logs.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;"><img src="image/folder.png" style="width:14px;" onclick="location.href='course_schedule.php'" style="cursor:pointer;"></a></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  onclick="location.href='credit_card_logs.php'" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Credit Card Logs</a></td>
                                </tr>
                                <?php if($checkndex != 4081){?>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideMeAccounts();ShowReceiptLogs();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMeAccounts();ShowReceiptLogs();" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Receipt Logs</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px;"></td>
                                    <td class="nopadd" style="padding:0px;">
                                    <div id="divreceiptreport" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="receipt_logs.php?receipt_type=internal" style="color:#3485a4;text-decoration:none;">Internal Students</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="receipt_logs.php?receipt_type=external" style="color:#3485a4;text-decoration:none;">External Examinee</a></td>
                                            </tr>
                                            <tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="receipt_logs.php?receipt_type=elp" style="color:#3485a4;text-decoration:none;">ELP Test</a></td>
                                            </tr>
                                   		</table>
                                   	</div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;" onclick="HideMeAccounts();ShowOnAccount();" style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a onclick="HideMeAccounts();ShowOnAccount();" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">On Account Report</a></td>
                                </tr>
                                <tr>
                                	<td class="nopadd" style="padding:0px;"></td>
                                    <td class="nopadd" style="padding:0px;">
                                    <div id="divonaccountreport" style="display:none;">
                                    	<table>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="onaccountreport.php?report_type=ee" style="color:#3485a4;text-decoration:none;">External Examinee</a></td>
                                            </tr>
                                        	<tr>
                                            	<td class="nopadd"><img src="image/smallarrow.png"></td>
                                                <td class="nopadd"><a href="onaccountreport.php?report_type=elp" style="color:#3485a4;text-decoration:none;">ELP Test</a></td>
                                            </tr>
                                   		</table>
                                   	</div>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  href="fi_hrs_revenue.php"  style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">FI Revenue Hrs</a>
                                    </td>
                                </tr>
                                <?php } ?>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  href="fi_hrs_revenue_new.php"  style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">FI Revenue Hrs - New Format</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  href="flight_training_incomehrs.php"  style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">Flight Training Income Hours</a>
                                    </td>
                                </tr>
                                <tr>
                                	<td class="nopadd" width="10"><img src="image/folder.png"  style="width:14px;"  style="cursor:pointer;"></td>
                                    <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  href="sentsms_activities.php"  style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;">SMS History Logs</a>
                                    </td>
                                </tr>
                            </table>
                       
                    </div>
                    <?php } 
					if($dept == "Engineering Instructors" || $dept == "Staff" || $dept == "staff"){  
					/*********encryption*************************/
					$l_secure_query = 'ndex='.$checkndex; 
					$l_encrypted = doEncrypt($l_secure_query); 
					/**********************************************/
					?>
               		<div style="width:20%;height:400px;border-right:solid 1px #8dcae3;">
                        <table>
                            <!--tr>
                                <td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='otherusers_view.php?<?php echo $l_encrypted; ?>'"><img src="image/folder.png"  style="width:14px;"></a></td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='otherusers_view.php?<?php echo $l_encrypted; ?>'">My Profile</a></td>
                            </tr-->
                            <?php if($dept == "Staff" || $dept == "staff"){?>
                            <tr>
                                <td class="nopadd" width="10">
                                    <a  style="cursor:pointer;font-size:12px;" href="employee_file.php?ndex=<?php echo $checkndex; ?>&sel_dept=1"><img src="image/folder.png"  style="width:14px;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;">
                                    <a  style="cursor:pointer;font-size:12px;color:#3485a4;text-decoration:none;" href="employee_file.php?ndex=<?php echo $checkndex; ?>&sel_dept=4">My HR Profile</a>
                                </td>
                            </tr>
                            <?php } ?>
                            <tr>
                                <td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='changepasswordadmin.php'"><img src="image/folder.png"  style="width:14px;"></a></td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='changepasswordadmin.php'">Change Password</a></td>
                            </tr>
                            <tr>
                                <td class="nopadd" style="padding:0px"></td>
                                <td class="nopadd" style="padding:0px">
                                <div style="display:none;" id="divstudmenu">
                                    <table>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="studselect.php" style="color:#3485a4;text-decoration:none;">Current Student</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="pendingstudent.php" style="color:#3485a4;text-decoration:none;">Pending Student</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="incompleteselect.php" style="color:#3485a4;text-decoration:none;">Unaccomplished Student</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="accomplishselect.php" style="color:#3485a4;text-decoration:none;">Accomplished Student</a></td>
                                        </tr>
                                    </table>
                                    </div>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" style="padding:0px"></td>
                                <td class="nopadd" style="padding:0px">
                                <div style="display:none;" id="divinsmenu">
                                    <table>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="insselect.php" style="color:#3485a4;text-decoration:none;">Current Instructor</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="pilotstatus.php" style="color:#3485a4;text-decoration:none;" target="_blank">Pilot's Status</a></td>
                                        </tr>
                                    </table>
                                    </div>
                                </td>
                            </tr>
                             <tr>
                                <td class="nopadd" style="padding:0px;"></td>
                                <td class="nopadd" style="padding:0px;">
                                	<div style="display:none;" id="divinsmenu">
                                    <table>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="insselect.php" style="color:#3485a4;text-decoration:none;">Current Instructor</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="addins.php" style="color:#3485a4;text-decoration:none;">Add New Instructor</a></td>
                                        </tr>
                                    </table>
                                    </div>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" style="padding:0px;"></td>
                                <td class="nopadd" style="padding:0px;"><div id="divquestion" style="display:none;"></div></td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="HideMeStaff();showrequest2();"><img src="image/folder.png"  style="width:14px;"></a></td>
                                <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a  style="cursor:pointer;font-size:12px;"  onclick="HideMeStaff();showrequest2();">Request Form</a></td>
                            </tr>
                            <tr>
                                <td class="nopadd" style="padding:0px;"></td>
                                <td class="nopadd" style="padding:0px;">
                                <div id="divrequestform2" style="display:none;">
                                    <table>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="passportreq.php" style="color:#3485a4;text-decoration:none;">Request for passport</a></td>
                                        </tr>
                                        <tr>
                                            <td class="nopadd"><img src="image/smallarrow.png"></td>
                                            <td class="nopadd"><a href="leavereq.php" style="color:#3485a4;text-decoration:none;">Request for Leave</a></td>
                                        </tr>
                                    </table>
                                </div>
                                </td>
                            </tr>
                            <tr>
                                <td class="nopadd" width="10" id="reqadmin">
                                    <a  style="cursor:pointer;font-size:12px;text-decoration:none" href="classroom_issues.php"><img src="image/folder.png"  style="width:14px;" onclick="HideMe3();HideMe();" style="cursor:pointer;"></a>
                                </td>
                                <td class="nopadd" style="font-size:14px;font-weight:bold;">
                                    <a  style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;" href="classroom_issues.php">Classroom Issue</a>
                                </td>
                            </tr>
                        </table>
                    </div>
                     <?php } 
                    /****************************** Michael access*******************************/
					 if($dept == "1i" &&($checkndex == 5696 || $checkndex == 8745 || $checkndex == 8746)){ ?>
               		<div style="width:20%;height:400px;border-right:solid 1px #8dcae3;">
                    <table>
                        <tr>
                            <td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='student_attendance_view.php'"><img src="image/folder.png"  style="width:14px;"></a></td>
                            <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='student_attendance_view.php'">View Daily Attendance</a></td>
                        </tr>
                        <tr>
                            <td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='student_attendance_subjects.php'"><img src="image/folder.png"  style="width:14px;"></a></td>
                            <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='student_attendance_subjects.php'">View Subject Attendance</a></td>
                        </tr>
                        <tr>
                            <td class="nopadd" width="10"><a style="cursor:pointer;font-size:12px;" onclick="location.href='student_attendance_all.php'"><img src="image/folder.png"  style="width:14px;"></a></td>
                            <td class="nopadd" style="font-size:14px;color:#3485a4;font-weight:bold;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='student_attendance_all.php'">View All Student Attendance</a></td>
                        </tr>
                     </table>
                     </div>
                        </td>
                        </tr>
                    </table>
                    </div>
                    <?php } 
					/****************************** End of Michael access*******************************/
					if($dept == "Admin/Flights"){?>
                    <div style="width:75%;">
                    	<table  style="margin-bottom:65px;">
                        	<tr>
                            	<td colspan="2" style="padding-bottom:0px;"> 
                                	<table style="padding:0px;">
                                    	<tr>
                                        	<td style="padding:0px;"><p style="font-size:15px;top:15px;font-weight:bold;color:#065777;">MAIN OPERATION</p></td>
                                            <td style="padding:0px;padding-left:5px;"><img src="image/arrowmain.jpg" style="float:right;"></td>
                                        </tr>
                                    </table>
                                </td>
                                <td style="padding-bottom:0px;"></td>
                            </tr>
                        	<tr>
                            	<td style="padding:25px;"><a href="#studentslink"><img src="image/studico.png" style="cursor:pointer;" onclick="HideAdministrator();showstudmenu();"></a></td>
                                <td style="padding:25px;"><a href="#intructorslink"><img src="image/instructor.png" style="cursor:pointer;" onclick="HideAdministrator();showinsmenu();"></a></td>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="HideAdministrator();showsms();"><img src="image/sms.png"></a></td>
                            </tr>
                            <tr>
                            	<td style="padding:25px;"><a href="#reqadmin"  style="cursor:pointer;font-size:12px;" onclick="HideAdministrator();showrequest();"><img src="image/approvalreq.png"></a></td>
                                <td style="padding:25px;"><a style="cursor:pointer;font-size:12px;" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex; ?>&username=<?php echo $userusername; ?>&password=<?php echo $userpassword; ?>&userdecided=1" class="lbOn"><img src="image/passwordchange.png"></a></td>
                                <td style="padding:25px;"><a href="register_select.php"><img src="image/register.png" style="cursor:pointer;"></a></td>
                            </tr>
                        </table>
                    </div>
                    <?php } 
					if($dept == "Administrator"){?>
                    <div style="width:75%;padding:25px;" align="left">
                    <p style="font-size:15px;top:16px;font-weight:bold;color:#065777;">MAIN OPERATION <img src="image/arrowmain.jpg"><br/><br/></p>
					<?php /* if($checkndex == 3915){?>
                    <a href="#studentslink" style="padding:25px;padding-bottom:50px;"><img src="image/studico.png" style="cursor:pointer;" onclick="HideMe3();HideMe();showstudmenu();"></a>
                    <a href="#intructorslink" style="padding:25px;padding-bottom:50px;"><img src="image/instructor.png" style="cursor:pointer;" onclick="HideMe3();HideMe();showinsmenu();"></a>
                    <a style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" onclick="HideAdministrator();HideMe3();HideMe();showotherusers();"><img src="image/otherusers.png"></a>
                    <a href="register_select.php" style="padding:25px;padding-bottom:50px;cursor:pointer;"><img src="image/register.png"></a>
                    <a style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" onclick="HideMe3();HideMe();showadmindaily();"><img src="image/technicallog.png"></a>
                    <a href="contract_list_only_latest.php" style="padding:25px;padding-bottom:50px;"><img src="image/contracts.png" style="cursor:pointer;"></a>
                    <a href="loginquestion.php" class="lbOn" style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;"><img src="image/questionbank.png"></a>
                    <a style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" onclick="location.href='requested.php'"><img src="image/request.png"></a>
                    <a style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" onclick="HideMe3();showacmenu();"><img src="image/aircraft.png"></a>
                    <a  style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" onclick="location.href='addschedule.php'"><img src="image/addflightsched.png"></a>
                    <a  style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" onclick="location.href='activities.php'"><img src="image/activities.png"></a>
                    <a  style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" onclick="location.href='aircraftattachments.php'"><img src="image/aircraftdoc.png"></a>
                    <a  style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" onclick="location.href='dutytimefi_new.php'"><img src="image/dutytime2.png"></a>
                    <a href="#report"  style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;"  onclick="HideMe3();HideMe();showdaily();"><img src="image/reports.png"></a>
                    <a href="#reqadmin"  style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" onclick="HideMe3();HideMe();showrequest();"><img src="image/approvalreq.png"></a>
                    <a  style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex; ?>&username=<?php echo $userusername; ?>&password=<?php echo $userpassword; ?>&userdecided=1" class="lbOn"><img src="image/passwordchange.png"></a>
                    <a href="studentprogress_new.php"  style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;"><img src="image/studmonitor.png"></a>
                    <a href="#report2" onclick="HideMe3();HideMe();showsfoadmin();" style="padding:25px;padding-bottom:50px;"><img src="image/flightsafetyreport.png" style="cursor:pointer;"></a>
                    <a href="#marketing"  style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" onclick="HideMe3();HideMe();HideAdministrator();ShowMarketing();"><img src="image/marketing.png"></a>
                    <a href="add_instructions.php"  style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" onclick=""><img src="image/broadcast.png"></a>
                    <a  style="padding:25px;padding-bottom:50px;cursor:pointer;font-size:12px;" onclick="HideAdministrator();showsms();"><img src="image/sms.png"></a>
                    <a href="recurrent_exam.php" style="padding:25px;padding-bottom:50px;cursor:pointer;"><img src="image/recurrent_exam.png"></a>
                    <a href="check_security_expiry2.php" style="padding:25px;padding-bottom:50px;cursor:pointer;"><img src="image/security.png"></a>
                    <a href="elp.php" style="padding:25px;padding-bottom:50px;cursor:pointer;"><img src="image/elp.png"></a>
                    <a href="manuals.php" style="padding:25px;padding-bottom:50px;cursor:pointer;"><img src="image/manual.png"></a>
                    <?php }*/?>
                    	<table style="margin-bottom:65px;">
                        	<tr>
                            	<td style="padding:25px;"><a href="#studentslink"><img src="image/studico.png" style="cursor:pointer;" onclick="HideMe3();HideMe();showstudmenu();"></a></td>
                                <td style="padding:25px;"><a href="#intructorslink"><img src="image/instructor.png" style="cursor:pointer;" onclick="HideMe3();HideMe();showinsmenu();"></a></td>
                                <td style="padding:25px;"><a style="cursor:pointer;font-size:12px;" onclick="HideAdministrator();HideMe3();HideMe();showotherusers();"><img src="image/otherusers.png"></a></td>
                            	<td style="padding:25px;"><a href="register_select.php"><img src="image/register.png" style="cursor:pointer;"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='accounting.php'"><img src="image/accounting.png"></a></td>
                                <td style="padding:25px;"><a style="cursor:pointer;font-size:12px;" onclick="HideMe3();HideMe();showadmindaily();"><img src="image/technicallog.png"></a></td>
                            	<td style="padding:25px;"><a href="contract_list_only_latest.php"><img src="image/contracts.png" style="cursor:pointer;"></a></td>
                                <td style="padding:25px;"><a href="loginquestion.php" class="lbOn" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;"><img src="image/questionbank.png"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='requested.php'"><img src="image/request.png"></a></td>
                            	<td style="padding:25px;"><a style="cursor:pointer;font-size:12px;" onclick="HideMe3();showacmenu();"><img src="image/aircraft.png"></a></td>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='addschedule.php'"><img src="image/addflightsched.png"></a></td>
                               <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='activities.php'"><img src="image/activities.png"></a></td>
                            </tr>
                            <tr>
                            	<td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='aircraftattachments.php'"><img src="image/aircraftdoc.png"></a></td>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='dutytimefi_new.php'"><img src="image/dutytime2.png"></a></td>
                                <td style="padding:25px;"><a href="#report"  style="cursor:pointer;font-size:12px;"  onclick="HideMe3();HideMe();showdaily();"><img src="image/reports.png"></a></td>
                            	<td style="padding:25px;"><a href="#reqadmin"  style="cursor:pointer;font-size:12px;" onclick="HideMe3();HideMe();showrequest();"><img src="image/approvalreq.png"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex; ?>&username=<?php echo $userusername; ?>&password=<?php echo $userpassword; ?>&userdecided=1" class="lbOn"><img src="image/passwordchange.png"></a></td>
                                <td style="padding:25px;"><a href="studentprogress_new.php"  style="cursor:pointer;font-size:12px;"><img src="image/studmonitor.png"></a></td>
                            	<td style="padding:25px;"><a href="#report2" onclick="HideMe3();HideMe();showsfoadmin();"><img src="image/flightsafetyreport.png" style="cursor:pointer;"></a></td>
                                <td style="padding:25px;"><a href="#marketing"  style="cursor:pointer;font-size:12px;" onclick="HideMe3();HideMe();HideAdministrator();ShowMarketing();"><img src="image/marketing.png"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a href="add_instructions.php"  style="cursor:pointer;font-size:12px;" onclick=""><img src="image/broadcast.png"></a></td>
                            	<td style="padding:25px;"><a href="recurrent_exam.php"><img src="image/recurrent_exam.png" style="cursor:pointer;"></a></td>
                                <td style="padding:25px;"><a href="check_security_expiry2.php"><img src="image/security.png" style="cursor:pointer;"></a></td>
                            	<td style="padding:25px;"><a href="manuals.php"><img src="image/manual.png" style="cursor:pointer;"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a href="elp.php"><img src="image/elp.png" style="cursor:pointer;"></a></td>
                                <?php if($checkndex == 3915 || $checkndex == 159 || $checkndex == 3945 || $checkndex == 28){?>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="HideAdministrator();showsms();"><img src="image/sms.png"></a></td>
                                <?php }?>
                            	<!--td style="padding:25px;"><a href="phone_activities.php"><img src="image/phone_activities.png" style="cursor:pointer;"></a></td>
                                <td style="padding:25px;"><img src="image/maintenance.png"></td-->
                            </tr>
                        </table>
                    </div>
                   <?php }
				   if($dept == "1"){?>
                    <div style="width:75%;">
                    	<table  style="margin-bottom:65px;">
                        	<tr>
                            	<td colspan="2" style="padding-bottom:0px;"> 
                                	<table style="padding:0px;">
                                    	<tr>
                                        	<td style="padding:0px;"><p style="font-size:15px;top:15px;font-weight:bold;color:#065777;">MAIN OPERATION</p></td>
                                            <td style="padding:0px;padding-left:5px;"><img src="image/arrowmain.jpg" style="float:right;"></td>
                                        </tr>
                                    </table>
                                </td>
                                <td style="padding-bottom:0px;"></td>
                            </tr>
                        	<tr>
                            	<td style="padding:25px;"><a onclick="HideMe2();showcourse();" style="cursor:pointer"><img src="image/myrecord.png"></a></td>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='technicallog.php'"><img src="image/technicallog.png"></a></td>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="showexam();"><img src="image/exam.png"></a></td>
                            	<td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='request.php'"><img src="image/request.png"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='viewtechlog.php'"><img src="image/checktechlog.png"></a></td>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='aircraftattachments.php'" target="_blank"><img src="image/aircraftdoc.png"></a></td>
                            	<td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='adddefect.php'"><img src="image/adddefect.png"></a></td>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='changepasswordstud.php'"><img src="image/passwordchange.png"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="HideMe2();showrequest();"><img src="image/approvalreq.png"></a></td>
                            	<td style="padding:25px;"><a href="#reportstud" onclick="HideMe2();showsfostud();"><img src="image/flightsafetyreport.png" style="cursor:pointer;"></a></td>
                                <td style="padding:25px;"><a href="new_message_list.php"><img src="image/messages.png" style="cursor:pointer;"></a></td>
                                <td style="padding:25px;"><a href="manuals.php"><img src="image/manual.png" style="cursor:pointer;"></a></td>
                            </tr>
                        </table>
                    </div>
                    <?php } 
					if($dept == "1i" && $checkndex != 5696 && $checkndex != 8745 && $checkndex != 8746 && $checkndex != 8790){?>
                    <div style="width:75%;">
                    	<table  style="margin-bottom:65px;">
                        	<tr>
                            	<td colspan="2" style="padding-bottom:0px;"> 
                                	<table style="padding:0px;">
                                    	<tr>
                                        	<td style="padding:0px;"><p style="font-size:15px;top:15px;font-weight:bold;color:#065777;">MAIN OPERATION</p></td>
                                            <td style="padding:0px;padding-left:5px;"><img src="image/arrowmain.jpg" style="float:right;"></td>
                                        </tr>
                                    </table>
                                </td>
                                <td style="padding-bottom:0px;"></td>
                            </tr>
                        	<tr>
                            	<td style="padding:25px;"><img src="image/studico.png" style="cursor:pointer;" onclick="HideMe();showstudmenu();"></td>
                                <td style="padding:25px;"><?php if($chiefins == "1"  || $hot == "1"){?>
                                	<a href="insselect.php"><img src="image/instructor.png" style="cursor:pointer;" onclick="HideMe();showinsmenu();"></a>
                                    <?php } ?>
                                </td>
                                <td style="padding:25px;">
                                <a onclick="location.href='finsview.php?myuserid=<?php echo $checkndex; ?>'" style="cursor:pointer;font-size:12px;"><img src="image/myrecord.png" style="cursor:pointer;"></a></td>
                            	<td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='technicallog.php'"><img src="image/technicallog.png"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='viewtechlog.php'"><img src="image/checktechlog.png"></a></td>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='request.php'"><img src="image/request.png"></a></td>
                            	<td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='technicallog.php?picstud=1'"><img src="image/picstud.png"></a></td>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;text-decoration:none;" href='pilotstatus.php' target="_blank"><img src="image/pilotstat.png"></a></td>
                            </tr>
                            <tr>
                            	<td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='aircraftattachments.php'"><img src="image/aircraftdoc.png"></a></td>
                            	<td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='adddefect.php'"><img src="image/adddefect.png"></a></td>
                                <td style="padding:25px;"><a href="#insreq"><img src="image/approvalreq.png" style="cursor:pointer;" onclick="HideMe();showrequest();"></a></td>
                                <td style="padding:25px;"><a href="technicallog.php?imdispatch=1"><img src="image/dispatch.png" style="cursor:pointer;"></a></td>
                            </tr>
                            <tr>
                            	<td style="padding:25px;">
									<?php if($chiefins == "1" || $co == "1" || $dept == "Administrator"){?>
                                    <a href="studentprogress_new.php" style="cursor:pointer;font-size:12px;"><img src="image/studmonitor.png"></a>
                                    <?php } else { ?>
                                    <a href="studentprogress_new.php" style="cursor:pointer;font-size:12px;"><img src="image/studmonitor.png"></a>
                                    <?php } ?>
                                </td>
                            	<td style="padding:25px;">
                                	<a style="cursor:pointer;font-size:12px;" onclick="location.href='changepassword.php'"><img src="image/passwordchange.png"></a>
                                </td>
                                <td style="padding:25px;">
                                	<?php //if($chiefins == "1" || $hot == "1"){?>
                                	<a  href="dutytimefi_new.php"  style="cursor:pointer;font-size:12px;"><img src="image/flightdutytime.png"></a>
                                    <?php //} ?>
                                </td>
                                <td style="padding:25px;"><a href="loginquestion.php" class="lbOn" style="cursor:pointer;font-size:12px;text-decoration:none;color:#3485a4;"><img src="image/questionbank.png"></a></td>
                         	</tr>
                            <tr>
                                <td style="padding:25px;"><a href="#report" onclick="HideMe();showsfo();"><img src="image/flightsafetyreport.png" style="cursor:pointer;"></a></td>
                                <td style="padding:25px;"><a href="new_message_list.php"><img src="image/messages.png" style="cursor:pointer;"></a></td>
                            	<td style="padding:25px;">
                                <?php if($chiefins == "1"){?>
                                	<a href="add_instructions.php"  style="cursor:pointer;font-size:12px;" onclick=""><img src="image/broadcast.png"></a>
                                 <?php } ?>
                                </td>
                                <td style="padding:25px;">
                                <?php if($hot == "1"){?>
                                	<a href="register_select.php"><img src="image/student_applicants.png" style="cursor:pointer;"></a>
                                 <?php } ?>
                                </td>
                        	</tr> 
                            <tr>
                                <td style="padding:25px;"><a onclick="HideMeIns();ShowRecurrent();" href="#recurrent_id"><img src="image/recurrent_exam.png" style="cursor:pointer;"></a></td>
                            	<td style="padding:25px;"><a href="elp.php"><img src="image/elp.png" style="cursor:pointer;"></a></td>
                                <td style="padding:25px;"><a href="manuals.php"><img src="image/manual.png" style="cursor:pointer;"></a></td>
                            </tr>     
                        </table>
                    </div>
                    <?php }
					if($dept == "1i" && $checkndex == 8790){?>
                    <div style="width:75%;">
                    	<table  style="margin-bottom:65px;">
                        	<tr>
                            	<td colspan="2" style="padding-bottom:0px;"> 
                                	<table style="padding:0px;">
                                    	<tr>
                                        	<td style="padding:0px;"><p style="font-size:15px;top:15px;font-weight:bold;color:#065777;">MAIN OPERATION</p></td>
                                            <td style="padding:0px;padding-left:5px;"><img src="image/arrowmain.jpg" style="float:right;"></td>
                                        </tr>
                                    </table>
                                </td>
                                <td style="padding-bottom:0px;"></td>
                            </tr>
                        	<tr>
                            	<td style="padding:25px;"><img src="image/studico.png" style="cursor:pointer;" onclick="showstudmenu();"></td>
                                <td style="padding:25px;"><a href="insselect.php"><img src="image/instructor.png" style="cursor:pointer;" onclick="showinsmenu();"></a></td>
                            	<td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='technicallog.php'"><img src="image/technicallog.png"></a></td>
                            	<td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='aircraftattachments.php'"><img src="image/aircraftdoc.png"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" onclick="location.href='viewtechlog.php'"><img src="image/checktechlog.png"></a></td>
                                <td style="padding:25px;"><a  href="dutytimefi_new.php"  style="cursor:pointer;font-size:12px;"><img src="image/flightdutytime.png"></a></td>
                                <td style="padding:25px;"><a  href="dutytime_students.php"  style="cursor:pointer;font-size:12px;"><img src="image/studdutytime.png"></a></td>
                                <td style="padding:25px;"><a href="manuals.php"><img src="image/manual.png" style="cursor:pointer;"></a></td>
                            </tr>     
                        </table>
                    </div>
                    <?php }
					if($dept == "Accounting"){?>
                    <div style="width:75%;">
                    	<table  style="margin-bottom:65px;float:left;">
                        	<tr>
                            	<td colspan="2" style="padding-bottom:0px;"> 
                                	<table style="padding:0px;">
                                    	<tr>
                                        	<td style="padding:0px;"><p style="font-size:15px;top:15px;font-weight:bold;color:#065777;">MAIN OPERATION</p></td>
                                            <td style="padding:0px;padding-left:5px;"><img src="image/arrowmain.jpg" style="float:right;"></td>
                                        </tr>
                                    </table>
                                </td>
                                <td style="padding-bottom:0px;"></td>
                            </tr>
                        	<tr>
                            	<td style="padding:25px;"><img src="image/studico.png" style="cursor:pointer;" onclick="HideMeAccounts();showstudmenu();"></td>
                                <td style="padding:25px;"><a href="#intructorslink"><img src="image/instructor.png" style="cursor:pointer;" onclick="HideMeAccounts();showinsmenu();"></a></td>
                                <td style="padding:25px;"><a onclick="location.href='accounting.php?myuserid=<?php echo $checkndex; ?>'" style="cursor:pointer;font-size:12px;"><img src="image/accounting.png" style="cursor:pointer;" onclick="HideMe();showinsmenu();"></a></td>
                            	<td style="padding:25px;"><a href="aircraftreceiving.php"><img src="image/partsprice.png" style="cursor:pointer;"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a onclick="HideMeAccounts();showrequest2();" style="cursor:pointer;"><img src="image/approvalreq.png" style="cursor:pointer;"></a></td>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex; ?>&username=<?php echo $userusername; ?>&password=<?php echo $userpassword; ?>&userdecided=1" class="lbOn"><img src="image/passwordchange.png"></a></td>
                            	<td style="padding:25px;"><a href="preflightauthorizationcheck.php"><img src="image/pendingpayment.png" style="cursor:pointer;"></a></td>
                                <td style="padding:25px;"><a href="register_select.php"><img src="image/student_applicants.png" style="cursor:pointer;"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a href="contract_list_only_latest.php"><img src="image/contracts.png" style="cursor:pointer;"></a></td>
                            </tr>
                        </table>
                    </div>
                   <?php } 
				   if($dept == "Safety"){?>
                    <div style="width:75%;">
                        <table style="margin-bottom:65px;">
                            <tr>
                                <td colspan="2" style="padding-bottom:0px;"> 
                                    <table style="padding:0px;">
                                        <tr>
                                            <td style="padding:0px;"><p style="font-size:15px;top:15px;font-weight:bold;color:#065777;">MAIN OPERATION</p></td>
                                            <td style="padding:0px;padding-left:5px;"><img src="image/arrowmain.jpg" style="float:right;"></td>
                                        </tr>
                                    </table>
                                </td>
                                <td style="padding-bottom:0px;"></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a href="#studentslink"><img src="image/studico.png" style="cursor:pointer;" onclick="HideSafety();showstudmenu();"></a></td>
                                <td style="padding:25px;"><a href="#intructorslink"><img src="image/instructor.png" style="cursor:pointer;" onclick="HideSafety();showinsmenu();"></a></td>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" href="onloadchangepassword.php?dept=<?php echo $dept;?>&id=<?php echo $checkndex; ?>&username=<?php echo $userusername; ?>&password=<?php echo $userpassword; ?>&userdecided=1" class="lbOn"><img src="image/passwordchange.png"></a></td>
                                <td style="padding:25px;"><a  style="cursor:pointer;font-size:12px;" href="showsched.php" target="_blank"><img src="image/technicallog.png"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a style="cursor:pointer;font-size:12px;" onclick="HideSafety();showacmenu();"><img src="image/aircraft.png"></a></td>
                                <td style="padding:25px;"><a href="#report2" onclick="HideSafety();showsfoadmin();"><img src="image/flightsafetyreport.png" style="cursor:pointer;"></a></td>
                                <td style="padding:25px;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='aircraftattachments.php'"><img src="image/aircraftdoc.png"></a></td>
                                <td style="padding:25px;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='dutytimefi_new.php'"><img src="image/dutytime2.png"></a></td>
                            </tr>
                            <tr>
                                <td style="padding:25px;"><a href="#report"  style="cursor:pointer;font-size:12px;"  onclick="HideSafety();showdaily();"><img src="image/reports.png"></a></td>
                                <td style="padding:25px;"><a style="cursor:pointer;font-size:12px;" onclick="location.href='add_notams.php'"><img src="image/notams.png"></a></td>
                                <td style="padding:25px;"><a href="manuals.php"><img src="image/manual.png" style="cursor:pointer;"></a></td>
                            	<td style="padding:25px;"><a  href="studentprogress_new.php"  style="cursor:pointer;font-size:12px;"><img src="image/studmonitor.png"></a></td>
                            </tr>
                        </table>
                    </div>
            	<?php } ?>
            </div>
        </div>
        </center>
    </div>
<?php if($msg != ""){?>
<script type="text/javascript">
	alert("<?php echo $msg; ?>")
</script>
<?php } ?>       
</body>
</html>
