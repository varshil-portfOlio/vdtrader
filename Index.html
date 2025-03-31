<?php
function fetch_nifty_data() {
    $url = "https://www.nseindia.com/api/option-chain-indices?symbol=NIFTY";
    
    $headers = [
        "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/123.0.0.0 Safari/537.36",
        "Accept: application/json, text/javascript, */*; q=0.01",
        "Accept-Language: en-US,en;q=0.9",
        "Referer: https://www.nseindia.com/",
        "Origin: https://www.nseindia.com",  // Added Origin header
        "Connection: keep-alive"
    ];

    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL, $url);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
    curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
    curl_setopt($ch, CURLOPT_FOLLOWLOCATION, false);  // Disable Follow Location
    curl_setopt($ch, CURLOPT_COOKIEFILE, ""); // Fixes session issue
    curl_setopt($ch, CURLOPT_COOKIEJAR, "/tmp/cookies.txt"); // Save cookies
    
    $response = curl_exec($ch);
    $http_code = curl_getinfo($ch, CURLINFO_HTTP_CODE);
    curl_close($ch);

    if ($http_code != 200) {
        echo "Error fetching data. HTTP Status: $http_code\n";
        return false;
    }

    return json_decode($response, true);
}

function get_closest_strike_price($nifty_value, $optionChain) {
    $closest_strike = null;
    $min_diff = PHP_INT_MAX;

    foreach ($optionChain as $entry) {
        if (isset($entry['strikePrice'])) {
            $strike_price = $entry['strikePrice'];
            $diff = abs($nifty_value - $strike_price);
            if ($diff < $min_diff) {
                $min_diff = $diff;
                $closest_strike = $strike_price;
            }
        }
    }
    return $closest_strike;
}

// Fetch data from NSE API
$data = fetch_nifty_data();
if (!$data) {
    die("❌ Failed to fetch data. NSE might have blocked the request.");
}

// Extract option chain data
$optionChain = $data['records']['data'] ?? [];
$callData = [];
$putData = [];

foreach ($optionChain as $entry) {
    if (isset($entry['CE'])) {
        $callData[] = [
            'strike' => $entry['strikePrice'],
            'oi' => $entry['CE']['openInterest']
        ];
    }
    if (isset($entry['PE'])) {
        $putData[] = [
            'strike' => $entry['strikePrice'],
            'oi' => $entry['PE']['openInterest']
        ];
    }
}

// Assume Nifty value fetched from somewhere, or set manually for demonstration
$current_nifty_value = 17500;  // Replace with live data or fetch from the API
$closest_strike_price = get_closest_strike_price($current_nifty_value, $optionChain);
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nifty Option Chain</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f7f7f7;
            color: #333;
        }

        h2 {
            text-align: center;
            margin: 30px 0;
            color: #2C3E50;
        }

        .container {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            gap: 20px;
            padding: 20px;
        }

        .box {
            background-color: #fff;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
            overflow: hidden;
            width: 45%;
            min-width: 300px;
            padding: 20px;
            transition: all 0.3s ease;
        }

        .box:hover {
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
        }

        h3 {
            margin-top: 0;
            color: #2980B9;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 10px;
        }

        th, td {
            padding: 10px;
            text-align: center;
            border: 1px solid #ddd;
        }

        th {
            background-color: #f0f0f0;
            font-weight: 500;
        }

        td {
            background-color: #fff;
        }

        .current-strike {
            background-color: #2980B9;
            color: white;
            padding: 10px;
            text-align: center;
            border-radius: 5px;
            margin-bottom: 20px;
        }

        @media screen and (max-width: 768px) {
            .container {
                flex-direction: column;
                align-items: center;
            }

            .box {
                width: 90%;
            }
        }
    </style>
</head>
<body>
    <h2>Nifty Option Chain - Open Interest</h2>
    
    <!-- Display Current Strike Price -->
    <div class="current-strike">
        Current Strike Price: <?= htmlspecialchars($closest_strike_price) ?>
    </div>

    <div class="container">
        <div class="box">
            <h3>Call Options (CE)</h3>
            <table>
                <tr><th>Strike Price</th><th>Call OI</th></tr>
                <?php foreach ($callData as $row): ?>
                    <tr><td><?= htmlspecialchars($row['strike']) ?></td><td><?= htmlspecialchars($row['oi']) ?></td></tr>
                <?php endforeach; ?>
            </table>
        </div>
        <div class="box">
            <h3>Put Options (PE)</h3>
            <table>
                <tr><th>Strike Price</th><th>Put OI</th></tr>
                <?php foreach ($putData as $row): ?>
                    <tr><td><?= htmlspecialchars($row['strike']) ?></td><td><?= htmlspecialchars($row['oi']) ?></td></tr>
                <?php endforeach; ?>
            </table>
        </div>
    </div>
</body>
</html>
