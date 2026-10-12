<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>我的網頁作品集 | Portfolio</title>
    <!-- 引入 Tailwind CSS 方便響應式佈局 -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- 引入 Google Font - Noto Sans TC 與 Plus Jakarta Sans -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@300;400;500;600;700&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --sage-bg: #F4F6F4;
            --sage-card: #FFFFFF;
            --sage-primary: #556B2F;
            --sage-hover: #435424;
            --sage-soft: #E2E8E2;
            --sage-text: #2C3531;
            --sage-muted: #707C74;
            --sage-accent: #8A9A86;
            --locked-bg: #EAEAEA;
            --locked-border: #D1D5DB;
            --locked-text: #9CA3AF;
        }

        body {
            font-family: 'Plus Jakarta Sans', 'Noto Sans TC', sans-serif;
            background-color: var(--sage-bg);
            color: var(--sage-text);
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(138, 154, 134, 0.08) 0%, transparent 40%),
                radial-gradient(circle at 90% 80%, rgba(85, 107, 47, 0.08) 0%, transparent 40%);
            background-attachment: fixed;
            min-height: 100vh;
        }

        .bg-particle {
            position: fixed;
            border-radius: 50%;
            background: rgba(138, 154, 134, 0.15);
            pointer-events: none;
            z-index: 0;
            animation: floatSlow 12s infinite ease-in-out;
        }

        @keyframes floatSlow {
            0%, 100% { transform: translateY(0) scale(1); }
            50% { transform: translateY(-20px) scale(1.05); }
        }

        .card-unlocked {
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(8px);
            border: 1px solid rgba(138, 154, 134, 0.3);
            transition: all 0.35s cubic-bezier(0.34, 1.56, 0.64, 1);
            position: relative;
            overflow: hidden;
        }

        .card-unlocked:hover {
            transform: translateY(-6px) scale(1.02);
            border-color: var(--sage-primary);
            box-shadow: 0 12px 24px -8px rgba(85, 107, 47, 0.25);
        }

        /* 閃光流光效果 (Shimmer animation) */
        .card-unlocked::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(
                60deg,
                transparent 30%,
                rgba(255, 255, 255, 0.6) 50%,
                transparent 70%
            );
            transform: rotate(30deg) translateY(-100%);
            transition: transform 0.75s ease;
        }

        .card-unlocked:hover::after {
            transform: rotate(30deg) translateY(100%);
        }

        .card-locked {
            background: rgba(235, 238, 235, 0.6);
            border: 1px border-dashed var(--locked-border);
            color: var(--locked-text);
            cursor: not-allowed;
            user-select: none;
            transition: all 0.3s ease;
        }

        .card-locked:hover {
            background: rgba(225, 230, 225, 0.8);
            transform: translateY(-1px);
        }

        .badge-unlocked {
            background-color: rgba(85, 107, 47, 0.12);
            color: var(--sage-primary);
        }

        .badge-locked {
            background-color: rgba(156, 163, 175, 0.15);
            color: var(--locked-text);
        }

        /* 光暈擴散感 */
        .avatar-glow {
            box-shadow: 0 0 0 4px rgba(255, 255, 255, 0.8), 0 0 20px rgba(85, 107, 47, 0.18);
        }
    </style>
</head>
<body class="flex flex-col min-h-screen justify-between relative px-4 py-8 md:py-12">

    <!-- 背景動態優雅圓點飾品 -->
    <div class="bg-particle w-64 h-64 -top-10 -left-10" style="animation-delay: 0s;"></div>
    <div class="bg-particle w-96 h-96 -bottom-20 -right-20" style="animation-delay: -5s;"></div>

    <header class="max-w-4xl mx-auto w-full text-center mb-10 z-10">
        <!-- 大頭貼區域 -->
        <div class="relative inline-block mb-4">
            <img 
                src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?q=80&w=300&auto=format&fit=crop" 
                alt="Personal Avatar" 
                class="w-28 h-28 md:w-32 md:h-32 rounded-full object-cover avatar-glow mx-auto transition-transform duration-500 hover:scale-105"
            />
            <span class="absolute bottom-1 right-1 bg-emerald-600 border-2 border-white w-5 h-5 rounded-full flex items-center justify-center text-[10px] text-white shadow-sm" title="學習中">✓</span>
        </div>

        <!-- 姓名與簡介 -->
        <h1 class="text-2xl md:text-3xl font-bold tracking-tight text-[var(--sage-text)] mb-2">
            網頁程式設計作品集
        </h1>
        <p class="text-sm md:text-base text-[var(--sage-muted)] max-w-md mx-auto leading-relaxed font-light">
            🌱 記錄每一週的成長與關卡挑戰，持續累積網頁前端開發技巧。
        </p>

        <!-- 進度條條示 -->
        <div class="mt-6 max-w-xs mx-auto bg-white/80 p-2.5 rounded-2xl shadow-sm border border-emerald-900/5 flex items-center justify-between text-xs">
            <span class="text-[var(--sage-muted)]">總解鎖進度</span>
            <div class="w-32 bg-gray-200 h-2 rounded-full overflow-hidden">
                <div class="bg-[var(--sage-primary)] h-full rounded-full transition-all duration-1000" style="width: 12.5%;"></div>
            </div>
            <span class="font-semibold text-[var(--sage-primary)]">2 / 16</span>
        </div>
    </header>

    <main class="max-w-5xl mx-auto w-full flex-grow z-10 mb-12">
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 md:gap-5">

            <!-- ================= Week 1 (已解鎖) ================= -->
            <a href="w1/index.html" class="card-unlocked p-5 rounded-2xl flex flex-col justify-between h-36 group">
                <div class="flex items-center justify-between">
                    <span class="badge-unlocked text-[11px] font-semibold px-2.5 py-1 rounded-full flex items-center gap-1">
                        <span class="w-1.5 h-1.5 rounded-full bg-emerald-600 animate-ping"></span>
                        Week 01
                    </span>
                    <span class="text-lg text-[var(--sage-primary)] group-hover:scale-125 transition-transform duration-300">🔓</span>
                </div>
                <div>
                    <h2 class="font-semibold text-base text-[var(--sage-text)] group-hover:text-[var(--sage-primary)] transition-colors">
                        數位名片
                    </h2>
                    <p class="text-xs text-[var(--sage-muted)] mt-1 line-clamp-1">個人簡介與社交連結</p>
                </div>
            </a>

            <!-- ================= Week 2 (已解鎖) ================= -->
            <a href="w2/index.html" class="card-unlocked p-5 rounded-2xl flex flex-col justify-between h-36 group">
                <div class="flex items-center justify-between">
                    <span class="badge-unlocked text-[11px] font-semibold px-2.5 py-1 rounded-full flex items-center gap-1">
                        <span class="w-1.5 h-1.5 rounded-full bg-emerald-600"></span>
                        Week 02
                    </span>
                    <span class="text-lg text-[var(--sage-primary)] group-hover:scale-125 transition-transform duration-300">🔓</span>
                </div>
                <div>
                    <h2 class="font-semibold text-base text-[var(--sage-text)] group-hover:text-[var(--sage-primary)] transition-colors">
                        今天吃甚麼?
                    </h2>
                    <p class="text-xs text-[var(--sage-muted)] mt-1 line-clamp-1">美食選擇隨機抽籤器</p>
                </div>
            </a>

            <!-- ================= Week 3 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 03</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">任務鎖定中...</p>
                </div>
            </div>

            <!-- ================= Week 4 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 04</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">任務鎖定中...</p>
                </div>
            </div>

            <!-- ================= Week 5 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 05</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">任務鎖定中...</p>
                </div>
            </div>

            <!-- ================= Week 6 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 06</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">任務鎖定中...</p>
                </div>
            </div>

            <!-- ================= Week 7 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 07</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">任務鎖定中...</p>
                </div>
            </div>

            <!-- ================= Week 8 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 08</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">期中專案預留</p>
                </div>
            </div>

            <!-- ================= Week 9 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 09</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">任務鎖定中...</p>
                </div>
            </div>

            <!-- ================= Week 10 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 10</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">任務鎖定中...</p>
                </div>
            </div>

            <!-- ================= Week 11 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 11</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">任務鎖定中...</p>
                </div>
            </div>

            <!-- ================= Week 12 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 12</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">任務鎖定中...</p>
                </div>
            </div>

            <!-- ================= Week 13 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 13</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">任務鎖定中...</p>
                </div>
            </div>

            <!-- ================= Week 14 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 14</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">任務鎖定中...</p>
                </div>
            </div>

            <!-- ================= Week 15 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 15</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">尚未解鎖</h2>
                    <p class="text-[11px] opacity-40 mt-1">任務鎖定中...</p>
                </div>
            </div>

            <!-- ================= Week 16 (未解鎖) ================= -->
            <div class="card-locked p-5 rounded-2xl flex flex-col justify-between h-36">
                <div class="flex items-center justify-between">
                    <span class="badge-locked text-[11px] font-medium px-2.5 py-1 rounded-full">Week 16</span>
                    <span class="text-base opacity-60">🔒</span>
                </div>
                <div>
                    <h2 class="font-medium text-sm opacity-60">期末成果</h2>
                    <p class="text-[11px] opacity-40 mt-1">最終大挑戰</p>
                </div>
            </div>

        </div>
    </main>

    <footer class="text-center text-xs text-[var(--sage-muted)] z-10 py-4 border-t border-emerald-900/5">
        <p>© Web Development Course Project Hub. Made with 🌿 Sage Green Design.</p>
    </footer>

</body>
</html>
