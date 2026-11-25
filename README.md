# agriculture-managment-system
Agriculture Management System – Description An Agriculture Management System is a software application designed to help farmers manage and monitor their agricultural activities efficiently. It uses modern technology to simplify farming operations, improve productivity, reduce manual work, and increase crop production.  The system helps farmers .  T
agriculture managment system discription

Agriculture Management System – Description
An Agriculture Management System is a software application designed to help farmers manage and monitor their agricultural activities efficiently. It uses modern technology to simplify farming operations, improve productivity, reduce manual work, and increase crop production.

The system helps farmers manage important activities such as crop planning, soil management, irrigation, fertilizer usage, pest control, weather monitoring, and harvesting. It also provides information about crop prices, farming techniques, and agricultural resources.

Main Objectives
To simplify and improve farming activities.

To help farmers select suitable crops based on soil and weather conditions.

To manage irrigation and water resources effectively.

To provide information about fertilizers and pesticides.

To monitor crop growth and production.

To reduce farming costs and save time.

To increase agricultural productivity and farmers' income.vvvvv
<!DOCTYPE html>
<html>
<head>
    <title>Agriculture Management System</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: #f1f8e9;
        }

        header {
            background: #2e7d32;
            color: white;
            padding: 20px;
            text-align: center;
        }

        nav {
            background: #1b5e20;
            padding: 15px;
            text-align: center;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin: 15px;
        }

        .container {
            padding: 25px;
        }

        .cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 20px;
        }

        .card {
            background: white;
            padding: 25px;
            text-align: center;
            border-radius: 10px;
            box-shadow: 0 2px 8px #ccc;
        }

        .card h2 {
            color: #2e7d32;
        }

        input, select, button {
            padding: 10px;
            margin: 5px;
            border: 1px solid #aaa;
            border-radius: 5px;
        }

        button {
            background: #2e7d32;
            color: white;
            cursor: pointer;
        }

        table {
            width: 100%;
            background: white;
            margin-top: 20px;
            border-collapse: collapse;
        }

        th, td {
            border: 1px solid #ddd;
            padding: 12px;
            text-align: center;
        }

        th {
            background: #388e3c;
            color: white;
        }
    </style>
</head>

<body>

<header>
    <h1>🌾 Agriculture Management System</h1>
    <p>Smart Farming Management Dashboard</p>
</header>

<nav>
    <a href="#dashboard">Dashboard</a>
    <a href="#crops">Crop Management</a>
    <a href="#farmers">Farmer Management</a>
</nav>

<div class="container">

    <h2 id="dashboard">Dashboard</h2>

    <div class="cards">
        <div class="card">
            <h2 id="farmerCount">0</h2>
            <p>Total Farmers</p>
        </div>

        <div class="card">
            <h2 id="cropCount">0</h2>
            <p>Total Crops</p>
        </div>

        <div class="card">
            <h2>🌱</h2>
            <p>Smart Farming</p>
        </div>
    </div>

    <h2 id="farmers">Add Farmer Details</h2>

    <input type="text" id="farmerName"
           placeholder="Farmer Name">

    <input type="text" id="farmerPhone"
           placeholder="Phone Number">

    <input type="text" id="farmerLocation"
           placeholder="Village / Location">

    <button onclick="addFarmer()">Add Farmer</button>

    <table>
        <thead>
            <tr>
                <th>Name</th>
                <th>Phone</th>
                <th>Location</th>
                <th>Action</th>
            </tr>
        </thead>
        <tbody id="farmerTable"></tbody>
    </table>

    <h2 id="crops">Crop Management</h2>

    <input type="text" id="cropName"
           placeholder="Crop Name">

    <select id="cropSeason">
        <option value="">Select Season</option>
        <option>Kharif</option>
        <option>Rabi</option>
        <option>Zaid</option>
    </select>

    <input type="number" id="cropArea"
           placeholder="Land Area (Acres)">

    <button onclick="addCrop()">Add Crop</button>

    <table>
        <thead>
            <tr>
                <th>Crop Name</th>
                <th>Season</th>
                <th>Land Area</th>
                <th>Action</th>
            </tr>
        </thead>
        <tbody id="cropTable"></tbody>
    </table>

</div>

<script>
    let farmers = [];
    let crops = [];

    function addFarmer() {
        let name = document.getElementById("farmerName").value;
        let phone = document.getElementById("farmerPhone").value;
        let location = document.getElementById("farmerLocation").value;

        if (!name || !phone || !location) {
            alert("Please fill all farmer details");
            return;
        }

        farmers.push({name, phone, location});

        document.getElementById("farmerName").value = "";
        document.getElementById("farmerPhone").value = "";
        document.getElementById("farmerLocation").value = "";

        displayFarmers();
    }

    function displayFarmers() {
        let table = document.getElementById("farmerTable");
        table.innerHTML = "";

        farmers.forEach((farmer, index) => {
            table.innerHTML += `
                <tr>
                    <td>${escapeHTML(farmer.name)}</td>
                    <td>${escapeHTML(farmer.phone)}</td>
                    <td>${escapeHTML(farmer.location)}</td>
                    <td><button onclick="deleteFarmer(${index})">Delete</button></td>
                </tr>`;
        });

        document.getElementById("farmerCount").innerText = farmers.length;
    }

    function deleteFarmer(index) {
        farmers.splice(index, 1);
        displayFarmers();
    }

    function addCrop() {
        let name = document.getElementById("cropName").value;
        let season = document.getElementById("cropSeason").value;
        let area = document.getElementById("cropArea").value;

        if (!name || !season || !area || Number(area) <= 0) {
            alert("Please enter valid crop details");
            return;
        }

        crops.push({name, season, area});

        document.getElementById("cropName").value = "";
        document.getElementById("cropSeason").value = "";
        document.getElementById("cropArea").value = "";

        displayCrops();
    }

    function displayCrops() {
        let table = document.getElementById("cropTable");
        table.innerHTML = "";

        crops.forEach((crop, index) => {
            table.innerHTML += `
                <tr>
                    <td>${escapeHTML(crop.name)}</td>
                    <td>${escapeHTML(crop.season)}</td>
                    <td>${escapeHTML(crop.area)} Acres</td>
                    <td><button onclick="deleteCrop(${index})">Delete</button></td>
                </tr>`;
        });

        document.getElementById("cropCount").innerText = crops.length;
    }

    function deleteCrop(index) {
        crops.splice(index, 1);
        displayCrops();
    }

    function escapeHTML(value) {
        return String(value).replace(/[&<>"']/g, char => ({
            '&': '&amp;',
            '<': '&lt;',
            '>': '&gt;',
            '"': '&quot;',
            "'": '&#39;'
        })[char]);
    }
</script>

</body>
</html>
