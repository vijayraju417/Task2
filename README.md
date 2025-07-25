# Task2
Intermediate HTML , Css and Js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Registration Form</title>
    <style>
        .form-container {
            max-width: 600px;
            margin: 40px auto;
            padding: 30px;
            background: linear-gradient(135deg, #ff7e5f, #feb47b);
            border-radius: 15px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            font-family: 'Verdana', sans-serif;
            color: #fff;
        }
        .form-group {
            margin-bottom: 25px;
        }
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            font-size: 16px;
        }
        input, select, textarea {
            width: 100%;
            padding: 12px;
            box-sizing: border-box;
            border: 2px solid #fff;
            border-radius: 8px;
            font-size: 14px;
            background-color: rgba(255, 255, 255, 0.9);
            color: #333;
            transition: border-color 0.3s ease;
        }
        input:focus, select:focus, textarea:focus {
            border-color: #ffd700;
            outline: none;
        }
        .error {
            color: #ff4444;
            font-size: 12px;
            display: none;
            margin-top: 5px;
        }
        button {
            padding: 12px 30px;
            background-color: #ffd700;
            color: #333;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: background-color 0.3s ease;
        }
        button:hover {
            background-color: #e6c200;
        }
        .success {
            display: none;
            color: #ffffff;
            text-align: center;
            margin-top: 15px;
            font-size: 16px;
            background-color: #4CAF50;
            padding: 10px;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div class="form-container">
        <form id="studentForm" onsubmit="return validateForm(event)">
            <div class="form-group">
                <label for="name">Full Name:</label>
                <input type="text" id="name" name="name" required>
                <span class="error" id="nameError">Name is required</span>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="email" name="email" required>
                <span class="error" id="emailError">Please enter a valid email</span>
            </div>
            <div class="form-group">
                <label for="rollNumber">Roll Number:</label>
                <input type="text" id="rollNumber" name="rollNumber" pattern="[A-Za-z0-9]{6,10}" required>
                <span class="error" id="rollNumberError">Roll number must be 6-10 alphanumeric characters</span>
            </div>
            <div class="form-group">
                <label for="requirements">Course Requirements:</label>
                <select id="requirements" name="requirements" required>
                    <option value="">Select a course</option>
                    <option value="computer_science">Computer Science</option>
                    <option value="mechanical_engineering">Mechanical Engineering</option>
                    <option value="electrical_engineering">Electrical Engineering</option>
                    <option value="business_administration">Business Administration</option>
                </select>
                <span class="error" id="requirementsError">Please select a course</span>
            </div>
            <div class="form-group">
                <label for="message">Additional Requirements:</label>
                <textarea id="message" name="message" rows="4" placeholder="Enter any specific requirements"></textarea>
                <span class="error" id="messageError">Additional requirements are required</span>
            </div>
            <button type="submit">Register</button>
            <div class="success" id="successMessage">Registration successful! Check your email for confirmation.</div>
        </form>
    </div>

    <script>
        function validateForm(event) {
            event.preventDefault();
            
            // Get form elements
            const name = document.getElementById('name').value.trim();
            const email = document.getElementById('email').value.trim();
            const rollNumber = document.getElementById('rollNumber').value.trim();
            const requirements = document.getElementById('requirements').value;
            const message = document.getElementById('message').value.trim();
            const nameError = document.getElementById('nameError');
            const emailError = document.getElementById('emailError');
            const rollNumberError = document.getElementById('rollNumberError');
            const requirementsError = document.getElementById('requirementsError');
            const messageError = document.getElementById('messageError');
            const successMessage = document.getElementById('successMessage');
            
            // Reset error and success messages
            nameError.style.display = 'none';
            emailError.style.display = 'none';
            rollNumberError.style.display = 'none';
            requirementsError.style.display = 'none';
            messageError.style.display = 'none';
            successMessage.style.display = 'none';

            // Validate name
            if (!name) {
                nameError.style.display = 'block';
                return false;
            }

            // Validate email
            const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (!emailPattern.test(email)) {
                emailError.style.display = 'block';
                return false;
            }

            // Validate roll number
            const rollNumberPattern = /^[A-Za-z0-9]{6,10}$/;
            if (!rollNumberPattern.test(rollNumber)) {
                rollNumberError.style.display = 'block';
                return false;
            }

            // Validate requirements
            if (!requirements || requirements === "") {
                requirementsError.style.display = 'block';
                return false;
            }

            // Validate message
            if (!message) {
                messageError.style.display = 'block';
                return false;
            }

            // If validation passes
            successMessage.style.display = 'block';
            return true;
        }
    </script>
</body>
</html>
