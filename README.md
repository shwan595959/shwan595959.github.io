<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galaxy Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0a0a0f;
            color: #fff;
            font-family: 'Segoe UI', sans-serif;
            overflow-x: hidden;
        }

        /* 별 배경 */
        .stars {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            pointer-events: none;
            z-index: 0;
        }

        .star {
            position: absolute;
            background: #fff;
            border-radius: 50%;
            animation: twinkle var(--duration) infinite alternate;
        }

        @keyframes twinkle {
            0%   { opacity: 0.2; transform: scale(1); }
            100% { opacity: 1;   transform: scale(1.4); }
        }

        /* 네비게이션 */
        nav {
            position: fixed;
            top: 0; left: 0; right: 0;
            z-index: 100;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 60px;
            background: rgba(10, 10, 20, 0.6);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(255,255,255,0.08);
        }

        .logo {
            font-size: 1.6rem;
            font-weight: 800;
            background: linear-gradient(135deg, #a78bfa, #60a5fa, #34d399);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: 2px;
        }

        .nav-links {
            display: flex;
            gap: 36px;
            list-style: none;
        }

        .nav-links a {
            color: rgba(255,255,255,0.7);
            text-decoration: none;
            font-size: 0.95rem;
            letter-spacing: 1px;
            transition: color 0.3s;
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -4px; left: 0;
            width: 0; height: 2px;
            background: linear-gradient(90deg, #a78bfa, #60a5fa);
            transition: width 0.3s;
        }

        .nav-links a:hover { color: #fff; }
        .nav-links a:hover::after { width: 100%; }

        /* 히어로 섹션 */
        .hero {
            position: relative;
            z-index: 1;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
        }

        .hero-badge {
            display: inline-block;
            padding: 6px 18px;
            border-radius: 50px;
            border: 1px solid rgba(167,139,250,0.4);
            background: rgba(167,139,250,0.1);
            font-size: 0.8rem;
            letter-spacing: 2px;
            color: #a78bfa;
            margin-bottom: 24px;
            animation: fadeInDown 0.8s ease;
        }

        .hero h1 {
            font-size: clamp(2.5rem, 7vw, 6rem);
            font-weight: 900;
            line-height: 1.1;
            margin-bottom: 24px;
            animation: fadeInUp 0.8s ease 0.2s both;
        }

        .gradient-text {
            background: linear-gradient(135deg, #a78bfa 0%, #60a5fa 50%, #34d399 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero p {
            font-size: 1.15rem;
            color: rgba(255,255,255,0.55);
            max-width: 520px;
            line-height: 1.8;
            margin-bottom: 40px;
            animation: fadeInUp 0.8s ease 0.4s both;
        }

        .btn-group {
            display: flex;
            gap: 16px;
            flex-wrap: wrap;
            justify-content: center;
            animation: fadeInUp 0.8s ease 0.6s both;
        }

        .btn-primary {
            padding: 14px 36px;
            border-radius: 50px;
            background: linear-gradient(135deg, #a78bfa, #60a5fa);
            color: #fff;
            font-size: 1rem;
            font-weight: 600;
            border: none;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
            box-shadow: 0 0 30px rgba(167,139,250,0.35);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 0 50px rgba(167,139,250,0.55);
        }

        .btn-secondary {
            padding: 14px 36px;
            border-radius: 50px;
            background: transparent;
            color: #fff;
            font-size: 1rem;
            font-weight: 600;
            border: 1px solid rgba(255,255,255,0.2);
            cursor: pointer;
            transition: all 0.2s;
        }

        .btn-secondary:hover {
            background: rgba(255,255,255,0.08);
            border-color: rgba(255,255,255,0.4);
            transform: translateY(-3px);
        }

        /* 플로팅 오브 */
        .orb {
            position: fixed;
            border-radius: 50%;
            filter: blur(80px);
            pointer-events: none;
            z-index: 0;
            animation: orbFloat 8s ease-in-out infinite alternate;
        }

        .orb-1 {
            width: 500px; height: 500px;
            background: rgba(167,139,250,0.15);
            top: -100px; left: -100px;
        }

        .orb-2 {
            width: 400px; height: 400px;
            background: rgba(96,165,250,0.12);
            bottom: -80px; right: -80px;
            animation-delay: -4s;
        }

        .orb-3 {
            width: 300px; height: 300px;
            background: rgba(52,211,153,0.1);
            top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            animation-delay: -2s;
        }

        @keyframes orbFloat {
            0%   { transform: translate(0, 0) scale(1); }
            100% { transform: translate(30px, 30px) scale(1.1); }
        }

        /* 카드 섹션 */
        .section {
            position: relative;
            z-index: 1;
            padding: 100px 60px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            text-align: center;
            font-size: 2.2rem;
            font-weight: 800;
            margin-bottom: 60px;
        }

        .cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 24px;
        }

        .card {
            background: rgba(255,255,255,0.04);
            border: 1px solid rgba(255,255,255,0.08);
            border-radius: 20px;
            padding: 36px 28px;
            transition: transform 0.3s, box-shadow 0.3s, border-color 0.3s;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0;
            height: 2px;
            background: var(--card-gradient);
            opacity: 0;
            transition: opacity 0.3s;
        }

        .card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 60px rgba(0,0,0,0.4);
            border-color: rgba(255,255,255,0.15);
        }

        .card:hover::before { opacity: 1; }

        .card-icon {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }

        .card h3 {
            font-size: 1.2rem;
            font-weight: 700;
            margin-bottom: 12px;
        }

        .card p {
            color: rgba(255,255,255,0.5);
            font-size: 0.92rem;
            line-height: 1.7;
        }

        /* 스탯 섹션 */
        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 24px;
            margin-top: 80px;
            padding: 50px;
            background: rgba(255,255,255,0.03);
            border: 1px solid rgba(255,255,255,0.07);
            border-radius: 24px;
        }

        .stat {
            text-align: center;
        }

        .stat-number {
            font-size: 3rem;
            font-weight: 900;
            background: linear-gradient(135deg, #a78bfa, #60a5fa);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .stat-label {
            color: rgba(255,255,255,0.45);
            font-size: 0.88rem;
            letter-spacing: 1px;
            margin-top: 6px;
        }

        /* 푸터 */
        footer {
            position: relative;
            z-index: 1;
            text-align: center;
            padding: 40px;
            color: rgba(255,255,255,0.25);
            font-size: 0.85rem;
            border-top: 1px solid rgba(255,255,255,0.06);
        }

        /* 애니메이션 */
        @keyframes fadeInDown {
            from { opacity: 0; transform: translateY(-20px); }
            to   { opacity: 1; transform: translateY(0); }
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to   { opacity: 1; transform: translateY(0); }
        }

        /* 스크롤바 */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #0a0a0f; }
        ::-webkit-scrollbar-thumb {
            background: linear-gradient(#a78bfa, #60a5fa);
            border-radius: 3px;
        }
    </style>
</head>
<body>

    <!-- 플로팅 오브 -->
    <div class="orb orb-1"></div>
    <div class="orb orb-2"></div>
    <div class="orb orb-3"></div>

    <!-- 별 배경 -->
    <div class="stars" id="stars"></div>

    <!-- 네비게이션 -->
    <nav>
        <div class="logo">NOVA</div>
        <ul class="nav-links">
            <li><a href="#">Home</a></li>
            <li><a href="#">About</a></li>
            <li><a href="#">Work</a></li>
            <li><a href="#">Contact</a></li>
        </ul>
    </nav>

    <!-- 히어로 -->
    <section class="hero">
        <div class="hero-badge">✦ WELCOME TO THE FUTURE ✦</div>
        <h1>
            Create Something<br>
            <span class="gradient-text">Extraordinary</span>
        </h1>
        <p>우주처럼 무한한 가능성을 탐험하세요.<br>당신의 아이디어를 현실로 만들어 드립니다.</p>
        <div class="btn-group">
            <button class="btn-primary">🚀 시작하기</button>
            <button class="btn-secondary">더 알아보기 →</button>
        </div>
    </section>

    <!-- 카드 섹션 -->
    <div class="section">
        <h2 class="section-title">✦ Our <span class="gradient-text">Services</span></h2>
        <div class="cards">
            <div class="card" style="--card-gradient: linear-gradient(90deg, #a78bfa, #60a5fa)">
                <div class="card-icon">🎨</div>
                <h3>UI/UX Design</h3>
                <p>사용자 경험을 최우선으로 생각하는 아름답고 직관적인 디자인을 제공합니다.</p>
            </div>
            <div class="card" style="--card-gradient: linear-gradient(90deg, #60a5fa, #34d399)">
                <div class="card-icon">⚡</div>
                <h3>Web Development</h3>
                <p>최신 기술 스택을 활용한 빠르고 안정적인 웹 애플리케이션을 개발합니다.</p>
            </div>
            <div class="card" style="--card-gradient: linear-gradient(90deg, #34d399, #fbbf24)">
                <div class="card-icon">🤖</div>
                <h3>AI Integration</h3>
                <p>인공지능 기술을 비즈니스에 접목하여 스마트한 솔루션을 만들어 드립니다.</p>
            </div>
            <div class="card" style="--card-gradient: linear-gradient(90deg, #fbbf24, #f87171)">
                <div class="card-icon">📱</div>
                <h3>Mobile App</h3>
                <p>iOS와 Android 모두를 아우르는 크로스 플랫폼 모바일 앱을 제작합니다.</p>
            </div>
        </div>

        <!-- 스탯 -->
        <div class="stats">
            <div class="stat">
                <div class="stat-number">200+</div>
                <div class="stat-label">PROJECTS DONE</div>
            </div>
            <div class="stat">
                <div class="stat-number">98%</div>
                <div class="stat-label">CLIENT SATISFACTION</div>
            </div>
            <div class="stat">
                <div class="stat-number">50+</div>
                <div class="stat-label">TEAM MEMBERS</div>
            </div>
            <div class="stat">
                <div class="stat-number">5★</div>
                <div class="stat-label">AVERAGE RATING</div>
            </div>
        </div>
    </div>

    <!-- 푸터 -->
    <footer>
        <p>© 2025 NOVA Studio · Made with ✦ and lots of ☕</p>
    </footer>

    <script>
        // 별 생성
        const starsContainer = document.getElementById('stars');
        for (let i = 0; i < 150; i++) {
            const star = document.createElement('div');
            star.classList.add('star');
            const size = Math.random() * 2.5 + 0.5;
            star.style.cssText = `
                width: ${size}px;
                height: ${size}px;
                top: ${Math.random() * 100}%;
                left: ${Math.random() * 100}%;
                --duration: ${Math.random() * 3 + 2}s;
                animation-delay: ${Math.random() * 3}s;
            `;
            starsContainer.appendChild(star);
        }

        // 마우스 시차 효과
        document.addEventListener('mousemove', (e) => {
            const x = (e.clientX / window.innerWidth - 0.5) * 20;
            const y = (e.clientY / window.innerHeight - 0.5) * 20;
            document.querySelector('.orb-1').style.transform =
                `translate(${x}px, ${y}px)`;
            document.querySelector('.orb-2').style.transform =
                `translate(${-x}px, ${-y}px)`;
        });

        // 카드 마우스 글로우 효과
        document.querySelectorAll('.card').forEach(card => {
            card.addEventListener('mousemove', (e) => {
                const rect = card.getBoundingClientRect();
                const x = ((e.clientX - rect.left) / rect.width) * 100;
                const y = ((e.clientY - rect.top) / rect.height) * 100;
                card.style.background =
                    `radial-gradient(circle at ${x}% ${y}%, rgba(255,255,255,0.07), rgba(255,255,255,0.03))`;
            });
            card.addEventListener('mouseleave', () => {
                card.style.background = 'rgba(255,255,255,0.04)';
            });
        });
    </script>
</body>
</html>
