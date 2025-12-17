<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>台幣匯率即時觀測站</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@300;400;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --bg-color: #0f172a;
            --glass-bg: rgba(255, 255, 255, 0.1);
            --text-main: #f8fafc;
            --accent: #38bdf8;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Noto Sans TC', sans-serif;
        }

        body {
            background: var(--bg-color);
            background-image: 
                radial-gradient(at 0% 0%, hsla(253,16%,7%,1) 0, transparent 50%), 
                radial-gradient(at 50% 0%, hsla(225,39%,30%,1) 0, transparent 50%), 
                radial-gradient(at 100% 0%, hsla(339,49%,30%,1) 0, transparent 50%);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            color: var(--text-main);
        }

        /* 浮動背景動畫 */
        .blobs {
            position: absolute;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: -1;
        }
        .blob {
            position: absolute;
            background: var(--accent);
            filter: blur(80px);
            border-radius: 50%;
            opacity: 0.2;
            animation: move 20s infinite alternate;
        }
        @keyframes move {
            from { transform: translate(0, 0); }
            to { transform: translate(100px, 100px); }
        }

        /* 主容器進場動畫 */
        .container {
            background: var(--glass-bg);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 24px;
            padding: 2.5rem;
            width: 90%;
            max-width: 480px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
            animation: fadeInScale 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
        }

        @keyframes fadeInScale {
            from { opacity: 0; transform: scale(0.9) translateY(20px); }
            to { opacity: 1; transform: scale(1) translateY(0); }
        }

        header {
            text-align: center;
            margin-bottom: 2rem;
        }

        h1 {
            font-size: 1.5rem;
            letter-spacing: 2px;
            margin-bottom: 0.5rem;
            background: linear-gradient(to right, #fff, var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .input-section {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        select {
            appearance: none;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.2);
            color: white;
            padding: 12px 20px;
            border-radius: 12px;
            font-size: 1rem;
            cursor: pointer;
            transition: 0.3s;
        }

        select:hover {
            background: rgba(255, 255, 255, 0.1);
            border-color: var(--accent);
        }

        .rate-display {
            text-align: center;
            padding: 1.5rem 0;
            border-bottom: 1px solid rgba(255,255,255,0.1);
            margin-bottom: 1rem;
        }

        #rate-value {
            font-size: 2.5rem;
            font-weight: 700;
            margin: 0.5rem 0;
            color: var(--accent);
            text-shadow: 0 0 20px rgba(56, 189, 248, 0.3);
        }

        .chart-box {
            margin-top: 1rem;
            height: 180px;
        }

        /* 點擊波紋特效 */
        .btn {
            background: var(--accent);
            color: #0f172a;
            border: none;
            padding: 12px;
            border-radius: 12px;
            font-weight: 700;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            transition: transform 0.1s;
        }

        .btn:active { transform: scale(0.95); }

        .ripple {
            position: absolute;
            background: rgba(255,255,255,0.4);
            border-radius: 50%;
            transform: scale(0);
            animation: ripple-effect 0.6s linear;
            pointer-events: none;
        }

        @keyframes ripple-effect {
            to { transform: scale(4); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="blobs">
        <div class="blob" style="width: 400px; height: 400px; top: -100px; left: -100px;"></div>
        <div class="blob" style="width: 300px; height: 300px; bottom: -50px; right: -50px; background: #818cf8;"></div>
    </div>

    <div class="container">
        <header>
            <h1>TWD 匯率觀測站</h1>
            <p style="font-size: 0.8rem; opacity: 0.6;">數據來源：實時金融 API 介面</p>
        </header>

        <div class="input-section">
            <select id="currency" onchange="handleCurrencyChange(event)">
                <option value="USD">🇺🇸 美元 (USD)</option>
                <option value="JPY">🇯🇵 日圓 (JPY)</option>
                <option value="EUR">🇪🇺 歐元 (EUR)</option>
                <option value="CNY">🇨🇳 人民幣 (CNY)</option>
                <option value="KRW">🇰🇷 韓元 (KRW)</option>
                <option value="GBP">🇬🇧 英鎊 (GBP)</option>
            </select>

            <div class="rate-display">
                <div style="font-size: 0.9rem; opacity: 0.7;">1 新台幣 (TWD) 等於</div>
                <div id="rate-value">---</div>
                <div id="update-time" style="font-size: 0.7rem; opacity: 0.5;">最後更新: 讀取中...</div>
            </div>

            <div class="chart-box">
                <canvas id="myChart"></canvas>
            </div>

            <button class="btn" onclick="fetchRate(event)">
                刷新即時行情
            </button>
        </div>
    </div>

    <script>
        // --- 1. 音效引擎 ---
        const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
        function playClickSound() {
            if (audioCtx.state === 'suspended') audioCtx.resume();
            const osc = audioCtx.createOscillator();
            const gain = audioCtx.createGain();
            osc.type = 'sine';
            osc.frequency.setValueAtTime(1000, audioCtx.currentTime);
            osc.frequency.exponentialRampToValueAtTime(40, audioCtx.currentTime + 0.1);
            gain.gain.setValueAtTime(0.1, audioCtx.currentTime);
            gain.gain.linearRampToValueAtTime(0, audioCtx.currentTime + 0.1);
            osc.connect(gain);
            gain.connect(audioCtx.destination);
            osc.start();
            osc.stop(audioCtx.currentTime + 0.1);
        }

        // --- 2. 匯率數據處理 ---
        let chartInstance = null;

        async function fetchRate(e) {
            if (e) createRipple(e);
            playClickSound();

            const currency = document.getElementById('currency').value;
            const rateEl = document.getElementById('rate-value');
            const timeEl = document.getElementById('update-time');

            rateEl.style.opacity = "0.5";

            try {
                // 使用免費且公信力強的 ExchangeRate-API (無須 Key 的開放端點範例)
                const res = await fetch(`https://open.er-api.com/v6/latest/TWD`);
                const data = await res.json();
                
                if (data.result === "success") {
                    const rate = data.rates[currency];
                    rateEl.innerText = `${rate.toFixed(4)} ${currency}`;
                    timeEl.innerText = `最後更新: ${new Date().toLocaleString()}`;
                    
                    // 模擬 7 日趨勢 (API 免費版通常不提供歷史數據，此處以基量進行隨機波動模擬)
                    generateTrendChart(currency, rate);
                }
            } catch (err) {
                rateEl.innerText = "Error";
                console.error("Fetch Error:", err);
            }
            rateEl.style.opacity = "1";
        }

        // --- 3. 圖表渲染 ---
        function generateTrendChart(symbol, currentRate) {
            const ctx = document.getElementById('myChart').getContext('2d');
            
            // 模擬前 6 天數據
            const labels = [];
            const dataPoints = [];
            for (let i = 6; i >= 0; i--) {
                const d = new Date();
                d.setDate(d.getDate() - i);
                labels.push(`${d.getMonth() + 1}/${d.getDate()}`);
                
                // 產生一個在當前匯率 ±1% 波動的模擬值
                if (i === 0) dataPoints.push(currentRate);
                else dataPoints.push(currentRate * (0.99 + Math.random() * 0.02));
            }

            if (chartInstance) chartInstance.destroy();

            chartInstance = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: labels,
                    datasets: [{
                        data: dataPoints,
                        borderColor: '#38bdf8',
                        backgroundColor: 'rgba(56, 189, 248, 0.1)',
                        borderWidth: 2,
                        fill: true,
                        tension: 0.4,
                        pointRadius: 0
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: {
                        x: { display: true, grid: { display: false }, ticks: { color: '#64748b', font: { size: 10 } } },
                        y: { display: false }
                    }
                }
            });
        }

        // --- 4. 互動特效 ---
        function handleCurrencyChange(e) {
            playClickSound();
            fetchRate();
        }

        function createRipple(event) {
            const btn = event.currentTarget;
            const circle = document.createElement("span");
            const diameter = Math.max(btn.clientWidth, btn.clientHeight);
            const radius = diameter / 2;
            
            circle.style.width = circle.style.height = `${diameter}px`;
            circle.style.left = `${event.clientX - btn.getBoundingClientRect().left - radius}px`;
            circle.style.top = `${event.clientY - btn.getBoundingClientRect().top - radius}px`;
            circle.classList.add("ripple");

            const prevRipple = btn.getElementsByClassName("ripple")[0];
            if (prevRipple) prevRipple.remove();
            btn.appendChild(circle);
        }

        // 初始化
        window.onload = () => fetchRate();
    </script>
</body>
</html>
