<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Miller's Planet Time Calculator</title>
</head>
<body>
    <h1>Miller's Planet Time Calculator</h1>
    <p>Enter the current date (or leave it blank to use today's date):</p>
    <input type="date" id="currentDate">
    <button onclick="calculateTime()">Calculate</button>

    <h3>Results:</h3>
    <p id="earthTime"></p>
    <p id="millersTime"></p>

    <script>
        function calculateTime() {
            const millersStart = new Date("2016-11-14"); // Date they reached Miller's Planet
            const currentDate = document.getElementById("currentDate").value 
                                ? new Date(document.getElementById("currentDate").value) 
                                : new Date(); // Use today's date if no input

            // Earth time difference
            const earthTimeMs = currentDate - millersStart;
            const earthDays = Math.floor(earthTimeMs / (1000 * 60 * 60 * 24));
            const earthYears = (earthDays / 365).toFixed(2);

            // Miller's time calculation
            const millersHours = (earthDays * 24) / (7 * 365 * 24);

            // Output results
            document.getElementById("earthTime").innerText = `Earth Time Passed: ${earthDays} days (${earthYears} years)`;
            document.getElementById("millersTime").innerText = `Miller's Time Passed: ${millersHours.toFixed(6)} hours`;
        }
    </script>
</body>
</html>
