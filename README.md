<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ID Card Generator</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f8f9fa;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
            box-sizing: border-box;
        }

        .container {
            width: 100%;
            max-width: 1000px;
            margin: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
        }

        .form-container {
            width: 100%;
            padding: 20px;
            background-color: #ffffff;
            border: 2px solid #007BFF;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            box-sizing: border-box;
            margin-bottom: 20px;
        }

        .form-container label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        .form-container input[type="text"],
        .form-container input[type="submit"],
        .form-container input[type="reset"],
        .form-container textarea,
        .form-container input[type="file"] {
            width: calc(100% - 20px);
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #007BFF;
            border-radius: 5px;
            box-sizing: border-box;
            font-size: 14px;
        }

        .form-container textarea {
            height: 60px;
            resize: vertical;
        }

        .form-container input[type="submit"],
        .form-container input[type="reset"] {
            cursor: pointer;
            background-color: #007BFF;
            color: white;
            border: none;
            transition: background-color 0.3s ease;
        }

        .form-container input[type="reset"] {
            background-color: #6c757d;
        }

        .form-container input[type="submit"]:hover,
        .form-container input[type="reset"]:hover {
            background-color: #0056b3;
        }

        .form-container input[type="reset"]:hover {
            background-color: #5a6268;
        }

        .id-card {
            display: none;
            width: 100%;
            max-width: 1000px;
            justify-content: center;
            align-items: center;
            box-sizing: border-box;
            margin-top: 20px; /* Add margin to separate from form */
        }

        .card-side {
            width: 45%;
            height: 350px; /* Increased height for better alignment */
            background-color: #ffffff;
            border: 2px solid #007BFF;
            border-radius: 10px;
            padding: 15px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            box-sizing: border-box;
            margin: 5px;
            display: flex;
            flex-direction: column;
            justify-content: space-between; /* Ensure content spaced correctly */
            align-items: center;
            position: relative; /* Added position relative for absolute positioning */
        }

        .card-side .header {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 10px;
        }

        .card-side .logo {
            width: 80px; /* Increased size */
            height: 80px; /* Increased size */
            border-radius: 10%;
            margin-right: 10px;
        }

        .card-side .student-photo {
            position: left;
            bottom: 10px; /* Adjust as needed */
            right: 10px; /* Adjust as needed */
            width: 120px; /* Increased size */
            height: 120px; /* Increased size */
            border-radius: 10%;
            border: 2px solid #007BFF;
            margin-bottom: 10px; /* Add margin to separate from other elements */
        }

        .card-side .content {
            width: 100%;
            text-align: left;
        }

        .card-side h2 {
            font-size: 20px;
            color: #007BFF;
            margin-bottom: 10px;
            text-align: center;
        }

        .card-side .college-name {
            color: #007BFF;
            font-weight: bold;
            margin-bottom: 10px;
            text-align: center;
        }

        .card-side p {
            margin: 5px 0;
            font-size: 14px;
            line-height: 1.5;
        }

        .form-container .note {
            font-size: 12px;
            color: #6c757d;
            margin-top: -10px;
            margin-bottom: 10px;
        }

        .terms {
            font-size: 12px;
            color: #6c757d;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Link to the Google Form -->
        <div class="form-link">
            <p>Please fill out the form to generate your ID card:</p>
            <a href="https://docs.google.com/forms/u/0/d/e/1FAIpQLSdHGzK7M_BRLKgZugftxJv4jilrcuvXjRkd5Fdo9Gw3aOwO0A/viewform" target="_blank">Fill out the form</a>
        </div>

        <!-- Your original form and ID card generator code can go here if needed -->
        <div class="form-container">
            <form id="idForm">
                <label for="studentName">Student Name:</label>
                <input type="text" id="studentName" name="studentName" required><br><br>
                
                <label for="usn">USN:</label>
                <input type="text" id="usn" name="usn" required><br><br>
                
                <label for="dob">Date of Birth:</label>
                <input type="text" id="dob" name="dob" required><br><br>
                
                <label for="fatherName">Father's Name:</label>
                <input type="text" id="fatherName" name="fatherName" required><br><br>
                
                <label for="validUpto">Valid Upto:</label>
                <input type="text" id="validUpto" name="validUpto" required><br><br>
                
                <label for="bloodGroup">Blood Group:</label>
                <input type="text" id="bloodGroup" name="bloodGroup" required><br><br>

                <label for="phoneNumber">Phone Number:</label>
                <input type="text" id="phoneNumber" name="phoneNumber" required><br><br>
                
                <label for="address">Address:</label>
                <textarea id="address" name="address" required></textarea><br><br>
                
                <label for="studentPhoto">Upload Student Photo (Max 2MB):</label>
                <input type="file" id="studentPhoto" name="studentPhoto" accept="image/*" required><br>
                <p class="note">Note: Photo should be less than 2MB.</p>

                <label for="studentSignature">Upload Student Signature (Max 2MB):</label>
                <input type="file" id="studentSignature" name="studentSignature" accept="image/*" required><br>
                <p class="note">Note: Signature should be less than 2MB.</p>
                
                <input type="submit" value="Generate ID Card">
                <input type="reset" value="Reset">
            </form>
        </div>

        <div class="id-card" id="idCard">
            <div class="card-side" id="cardFront">
                <div class="header">
                    <img src="logo.jpeg" alt="College Logo" class="logo">
                </div>
                <div class="content">
                    <h2 class="college-name">Government Engineering College Ramanagara-571401</h2>
                    <p><strong>Name:</strong> <span id="displayStudentName"></span></p>
                    <p><strong>USN:</strong> <span id="displayUsn"></span></p>
                    <p><strong>Date of Birth:</strong> <span id="displayDob"></span></p>
                    <p><strong>Blood Group:</strong> <span id="displayBloodGroup"></span></p>
                    <p><strong>Phone Number:</strong> <span id="displayPhoneNumber"></span></p>
                    <p><strong>Email:</strong> <span id="displayEmail"></span></p>
                    <img src="" alt="Student Photo" class="student-photo" id="displayStudentPhoto">
                </div>
            </div>
            <div class="card-side" id="cardBack">
                <div class="content">
                    <p><strong>Address:</strong> <span id="displayAddress"></span></p>
                    <img src="" alt="Student Signature" class="student-signature" id="displayStudentSignature">
                    <p class="terms">
                        <strong>Terms and Conditions:</strong><br>
                        This ID card is the property of the issuing institution and must be returned upon request. It is not transferable and must be carried at all times. Lost cards must be reported immediately.
                    </p>
                </div>
            </div>
        </div>
    </div>

    <script>
        document.getElementById('idForm').addEventListener('submit', function(event) {
            event.preventDefault();
            var studentName = document.getElementById('studentName').value;
            var usn = document.getElementById('usn').value;
            var dob = document.getElementById('dob').value;
            var fatherName = document.getElementById('fatherName').value;
            var validUpto = document.getElementById('validUpto').value;
            var bloodGroup = document.getElementById('bloodGroup').value;
            var phoneNumber = document.getElementById('phoneNumber').value;
            var address = document.getElementById('address').value;
            var studentPhoto = document.getElementById('studentPhoto').files[0];
            var studentSignature = document.getElementById('studentSignature').files[0];

            if (studentPhoto.size > 2 * 1024 * 1024 || studentSignature.size > 2 * 1024 * 1024) {
                alert('Photo and signature should be less than 2MB.');
                return;
            }

            document.getElementById('displayStudentName').innerText = studentName;
            document.getElementById('displayUsn').innerText = usn;
            document.getElementById('displayDob').innerText = dob;
            document.getElementById('displayBloodGroup').innerText = bloodGroup;
            document.getElementById('displayPhoneNumber').innerText = phoneNumber;
            document.getElementById('displayEmail').innerText = "abcdtechbd@gmail.com";
            document.getElementById('displayAddress').innerText = address;

            var readerPhoto = new FileReader();
            readerPhoto.onload = function(event) {
                document.getElementById('displayStudentPhoto').src = event.target.result;
            };
            readerPhoto.readAsDataURL(studentPhoto);

            var readerSignature = new FileReader();
            readerSignature.onload = function(event) {
                document.getElementById('displayStudentSignature').src = event.target.result;
            };
            readerSignature.readAsDataURL(studentSignature);

            document.getElementById('idCard').style.display = 'flex';
        });
    </script>
</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ID Card Generator</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f8f9fa;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
            box-sizing: border-box;
        }

        .container {
            width: 100%;
            max-width: 1000px;
            margin: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
        }

        .form-container {
            width: 100%;
            padding: 20px;
            background-color: #ffffff;
            border: 2px solid #007BFF;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            box-sizing: border-box;
            margin-bottom: 20px;
        }

        .form-container label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        .form-container input[type="text"],
        .form-container input[type="submit"],
        .form-container input[type="reset"],
        .form-container textarea,
        .form-container input[type="file"] {
            width: calc(100% - 20px);
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #007BFF;
            border-radius: 5px;
            box-sizing: border-box;
            font-size: 14px;
        }

        .form-container textarea {
            height: 60px;
            resize: vertical;
        }

        .form-container input[type="submit"],
        .form-container input[type="reset"] {
            cursor: pointer;
            background-color: #007BFF;
            color: white;
            border: none;
            transition: background-color 0.3s ease;
        }

        .form-container input[type="reset"] {
            background-color: #6c757d;
        }

        .form-container input[type="submit"]:hover,
        .form-container input[type="reset"]:hover {
            background-color: #0056b3;
        }

        .form-container input[type="reset"]:hover {
            background-color: #5a6268;
        }

        .id-card {
            display: none;
            width: 100%;
            max-width: 1000px;
            justify-content: center;
            align-items: center;
            box-sizing: border-box;
            margin-top: 20px; /* Add margin to separate from form */
        }

        .card-side {
            width: 45%;
            height: 350px; /* Increased height for better alignment */
            background-color: #ffffff;
            border: 2px solid #007BFF;
            border-radius: 10px;
            padding: 15px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            box-sizing: border-box;
            margin: 5px;
            display: flex;
            flex-direction: column;
            justify-content: space-between; /* Ensure content spaced correctly */
            align-items: center;
            position: relative; /* Added position relative for absolute positioning */
        }

        .card-side .header {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 10px;
        }

        .card-side .logo {
            width: 80px; /* Increased size */
            height: 80px; /* Increased size */
            border-radius: 10%;
            margin-right: 10px;
        }

        .card-side .student-photo {
            position: left;
            bottom: 10px; /* Adjust as needed */
            right: 10px; /* Adjust as needed */
            width: 120px; /* Increased size */
            height: 120px; /* Increased size */
            border-radius: 10%;
            border: 2px solid #007BFF;
            margin-bottom: 10px; /* Add margin to separate from other elements */
        }

        .card-side .content {
            width: 100%;
            text-align: left;
        }

        .card-side h2 {
            font-size: 20px;
            color: #007BFF;
            margin-bottom: 10px;
            text-align: center;
        }

        .card-side .college-name {
            color: #007BFF;
            font-weight: bold;
            margin-bottom: 10px;
            text-align: center;
        }

        .card-side p {
            margin: 5px 0;
            font-size: 14px;
            line-height: 1.5;
        }

        .form-container .note {
            font-size: 12px;
            color: #6c757d;
            margin-top: -10px;
            margin-bottom: 10px;
        }

        .terms {
            font-size: 12px;
            color: #6c757d;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Link to the Google Form -->
        <div class="form-link">
            <p>Please fill out the form to generate your ID card:</p>
            <a href="https://docs.google.com/forms/u/0/d/e/1FAIpQLSdHGzK7M_BRLKgZugftxJv4jilrcuvXjRkd5Fdo9Gw3aOwO0A/viewform" target="_blank">Fill out the form</a>
        </div>

        <!-- Your original form and ID card generator code can go here if needed -->
        <div class="form-container">
            <form id="idForm">
                <label for="studentName">Student Name:</label>
                <input type="text" id="studentName" name="studentName" required><br><br>
                
                <label for="usn">USN:</label>
                <input type="text" id="usn" name="usn" required><br><br>
                
                <label for="dob">Date of Birth:</label>
                <input type="text" id="dob" name="dob" required><br><br>
                
                <label for="fatherName">Father's Name:</label>
                <input type="text" id="fatherName" name="fatherName" required><br><br>
                
                <label for="validUpto">Valid Upto:</label>
                <input type="text" id="validUpto" name="validUpto" required><br><br>
                
                <label for="bloodGroup">Blood Group:</label>
                <input type="text" id="bloodGroup" name="bloodGroup" required><br><br>

                <label for="phoneNumber">Phone Number:</label>
                <input type="text" id="phoneNumber" name="phoneNumber" required><br><br>
                
                <label for="address">Address:</label>
                <textarea id="address" name="address" required></textarea><br><br>
                
                <label for="studentPhoto">Upload Student Photo (Max 2MB):</label>
                <input type="file" id="studentPhoto" name="studentPhoto" accept="image/*" required><br>
                <p class="note">Note: Photo should be less than 2MB.</p>

                <label for="studentSignature">Upload Student Signature (Max 2MB):</label>
                <input type="file" id="studentSignature" name="studentSignature" accept="image/*" required><br>
                <p class="note">Note: Signature should be less than 2MB.</p>
                
                <input type="submit" value="Generate ID Card">
                <input type="reset" value="Reset">
            </form>
        </div>

        <div class="id-card" id="idCard">
            <div class="card-side" id="cardFront">
                <div class="header">
                    <img src="logo.jpeg" alt="College Logo" class="logo">
                </div>
                <div class="content">
                    <h2 class="college-name">Government Engineering College Ramanagara-571401</h2>
                    <p><strong>Name:</strong> <span id="displayStudentName"></span></p>
                    <p><strong>USN:</strong> <span id="displayUsn"></span></p>
                    <p><strong>Date of Birth:</strong> <span id="displayDob"></span></p>
                    <p><strong>Blood Group:</strong> <span id="displayBloodGroup"></span></p>
                    <p><strong>Phone Number:</strong> <span id="displayPhoneNumber"></span></p>
                    <p><strong>Email:</strong> <span id="displayEmail"></span></p>
                    <img src="" alt="Student Photo" class="student-photo" id="displayStudentPhoto">
                </div>
            </div>
            <div class="card-side" id="cardBack">
                <div class="content">
                    <p><strong>Address:</strong> <span id="displayAddress"></span></p>
                    <img src="" alt="Student Signature" class="student-signature" id="displayStudentSignature">
                    <p class="terms">
                        <strong>Terms and Conditions:</strong><br>
                        This ID card is the property of the issuing institution and must be returned upon request. It is not transferable and must be carried at all times. Lost cards must be reported immediately.
                    </p>
                </div>
            </div>
        </div>
    </div>

    <script>
        document.getElementById('idForm').addEventListener('submit', function(event) {
            event.preventDefault();
            var studentName = document.getElementById('studentName').value;
            var usn = document.getElementById('usn').value;
            var dob = document.getElementById('dob').value;
            var fatherName = document.getElementById('fatherName').value;
            var validUpto = document.getElementById('validUpto').value;
            var bloodGroup = document.getElementById('bloodGroup').value;
            var phoneNumber = document.getElementById('phoneNumber').value;
            var address = document.getElementById('address').value;
            var studentPhoto = document.getElementById('studentPhoto').files[0];
            var studentSignature = document.getElementById('studentSignature').files[0];

            if (studentPhoto.size > 2 * 1024 * 1024 || studentSignature.size > 2 * 1024 * 1024) {
                alert('Photo and signature should be less than 2MB.');
                return;
            }

            document.getElementById('displayStudentName').innerText = studentName;
            document.getElementById('displayUsn').innerText = usn;
            document.getElementById('displayDob').innerText = dob;
            document.getElementById('displayBloodGroup').innerText = bloodGroup;
            document.getElementById('displayPhoneNumber').innerText = phoneNumber;
            document.getElementById('displayEmail').innerText = "abcdtechbd@gmail.com";
            document.getElementById('displayAddress').innerText = address;

            var readerPhoto = new FileReader();
            readerPhoto.onload = function(event) {
                document.getElementById('displayStudentPhoto').src = event.target.result;
            };
            readerPhoto.readAsDataURL(studentPhoto);

            var readerSignature = new FileReader();
            readerSignature.onload = function(event) {
                document.getElementById('displayStudentSignature').src = event.target.result;
            };
            readerSignature.readAsDataURL(studentSignature);

            document.getElementById('idCard').style.display = 'flex';
        });
    </script>
</body>
</html>
