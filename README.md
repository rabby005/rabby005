<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hassan Rabbi - Developer Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 100%);
            color: #fff;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .hero-content {
            text-align: center;
            z-index: 2;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1s ease forwards;
        }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero h1 {
            font-size: 4rem;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, #00d4ff, #7b2ff7);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero .subtitle {
            font-size: 1.5rem;
            color: #a0a0a0;
            margin-bottom: 2rem;
        }

        .typing-text {
            display: inline-block;
            border-right: 2px solid #00d4ff;
            animation: blink 0.7s infinite;
        }

        @keyframes blink {
            50% { border-color: transparent; }
        }

        /* Floating particles */
        .particle {
            position: absolute;
            background: radial-gradient(circle, #00d4ff 0%, transparent 70%);
            border-radius: 50%;
            pointer-events: none;
            animation: float 6s infinite ease-in-out;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0) translateX(0); }
            50% { transform: translateY(-20px) translateX(10px); }
        }

        /* Section Styles */
        .section {
            padding: 80px 0;
            opacity: 0;
            transform: translateY(50px);
            transition: all 0.8s ease;
        }

        .section.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .section-title {
            font-size: 2.5rem;
            margin-bottom: 3rem;
            text-align: center;
            position: relative;
            display: inline-block;
            width: 100%;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, #00d4ff, #7b2ff7);
            border-radius: 2px;
        }

        /* About Section */
        .about-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 2rem;
        }

        .about-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 30px;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .about-card:hover {
            transform: translateY(-10px);
            background: rgba(255, 255, 255, 0.1);
            box-shadow: 0 10px 40px rgba(0, 212, 255, 0.3);
        }

        .about-card h3 {
            color: #00d4ff;
            margin-bottom: 15px;
            font-size: 1.2rem;
        }

        /* Tech Stack */
        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
            gap: 20px;
            margin-top: 2rem;
        }

        .tech-item {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .tech-item:hover {
            transform: scale(1.1) rotate(5deg);
            background: rgba(123, 47, 247, 0.2);
            border-color: #7b2ff7;
        }

        .tech-item img {
            width: 50px;
            height: 50px;
            margin-bottom: 10px;
            filter: grayscale(100%);
            transition: filter 0.3s ease;
        }

        .tech-item:hover img {
            filter: grayscale(0%);
        }

        /* Social Links */
        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            margin-top: 2rem;
        }

        .social-link {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            width: 60px;
            height: 60px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
            text-decoration: none;
            color: #fff;
            font-size: 1.5rem;
        }

        .social-link:hover {
            transform: translateY(-5px);
            background: linear-gradient(45deg, #00d4ff, #7b2ff7);
            box-shadow: 0 10px 30px rgba(0, 212, 255, 0.5);
        }

        /* Stats Section */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 2rem;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 20px;
            overflow: hidden;
        }

        .stat-card img {
            width: 100%;
            border-radius: 10px;
            transition: transform 0.3s ease;
        }

        .stat-card:hover img {
            transform: scale(1.05);
        }

        /* CTA Button */
        .cta-button {
            display: inline-block;
            padding: 15px 40px;
            background: linear-gradient(45deg, #00d4ff, #7b2ff7);
            color: #fff;
            text-decoration: none;
            border-radius: 30px;
            font-weight: bold;
            transition: all 0.3s ease;
            margin-top: 2rem;
        }

        .cta-button:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 40px rgba(0, 212, 255, 0.5);
        }

        /* Scroll Indicator */
        .scroll-indicator {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateX(-50%) translateY(0); }
            40% { transform: translateX(-50%) translateY(-10px); }
            60% { transform: translateX(-50%) translateY(-5px); }
        }

        .scroll-indicator::before {
            content: '↓';
            font-size: 2rem;
            color: #00d4ff;
        }

        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }
            .hero .subtitle {
                font-size: 1.2rem;
            }
            .section-title {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <h1>Hassan Rabbi</h1>
            <p class="subtitle">Full Stack Developer | <span class="typing-text" id="typing"></span></p>
            <div class="social-links">
                <a href="https://github.com/rabby005" class="social-link" title="GitHub">GH</a>
                <a href="https://linkedin.com/in/hasssan-rabbi" class="social-link" title="LinkedIn">IN</a>
                <a href="https://facebook.com/farabyabdulla.alrabby.1" class="social-link" title="Facebook">FB</a>
                <a href="https://x.com/faraby55" class="social-link" title="X/Twitter">X</a>
                <a href="https://medium.com/@Rabbi-Hossain" class="social-link" title="Medium">M</a>
                <a href="https://youtube.com/@UCqzMhFWGgOrmLPv7_7a0Zrg" class="social-link" title="YouTube">YT</a>
                <a href="mailto:farabyabdulla@gmail.com" class="social-link" title="Email">✉</a>
            </div>
            <a href="#about" class="cta-button">Explore My Work</a>
        </div>
        <div class="scroll-indicator"></div>
    </section>

    <div class="container">
        <!-- About Section -->
        <section class="section" id="about">
            <h2 class="section-title">💫 About Me</h2>
            <div class="about-grid">
                <div class="about-card">
                    <h3>🔭 Current Focus</h3>
                    <p>Working on exciting Web Development projects</p>
                </div>
                <div class="about-card">
                    <h3>👯 Collaboration</h3>
                    <p>Looking to collaborate on Web Development projects</p>
                </div>
                <div class="about-card">
                    <h3>🌱 Learning</h3>
                    <p>Currently mastering Python</p>
                </div>
                <div class="about-card">
                    <h3>💡 Expertise</h3>
                    <p>Full Stack Development with modern technologies</p>
                </div>
            </div>
        </section>

        <!-- Tech Stack Section -->
        <section class="section">
            <h2 class="section-title">💻 Tech Stack</h2>
            <div class="tech-grid">
                <div class="tech-item">
                    <div style="font-size: 40px;">⚛️</div>
                    <p>React</p>
                </div>
                <div class="tech-item">
                    <div style="font-size: 40px;">🟨</div>
                    <p>JavaScript</p>
                </div>
                <div class="tech-item">
                    <div style="font-size: 40px;">🔷</div>
                    <p>TypeScript</p>
                </div>
                <div class="tech-item">
                    <div style="font-size: 40px;">🐍</div>
                    <p>Python</p>
                </div>
                <div class="tech-item">
                    <div style="font-size: 40px;">🟩</div>
                    <p>Node.js</p>
                </div>
                <div class="tech-item">
                    <div style="font-size: 40px;">🍃</div>
                    <p>MongoDB</p>
                </div>
                <div class="tech-item">
                    <div style="font-size: 40px;">☁️</div>
                    <p>AWS</p>
                </div>
                <div class="tech-item">
                    <div style="font-size: 40px;">🎨</div>
                    <p>CSS3</p>
                </div>
                <div class="tech-item">
                    <div style="font-size: 40px;">📱</div>
                    <p>HTML5</p>
                </div>
                <div class="tech-item">
                    <div style="font-size: 40px;">🔧</div>
                    <p>Git</p>
                </div>
                <div class="tech-item">
                    <div style="font-size: 40px;">🚀</div>
                    <p>Vite</p>
                </div>
                <div class="tech-item">
                    <div style="font-size: 40px;">🎯</div>
                    <p>Redux</p>
                </div>
            </div>
        </section>

        <!-- GitHub Stats Section -->
        <section class="section">
            <h2 class="section-title">📊 GitHub Statistics</h2>
            <div class="stats-grid">
                <div class="stat-card">
                    <img src="https://github-readme-stats.vercel.app/api?username=rabby005&theme=tokyonight&hide_border=true&include_all_commits=true&count_private=false" alt="GitHub Stats">
                </div>
                <div class="stat-card">
                    <img src="https://nirzak-streak-stats.vercel.app/?user=rabby005&theme=tokyonight&hide_border=true" alt="GitHub Streak">
                </div>
                <div class="stat-card">
                    <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=rabby005&theme=tokyonight&hide_border=true&include_all_commits=true&count_private=false&layout=compact" alt="Top Languages">
                </div>
            </div>
        </section>

        <!-- Trophies Section -->
        <section class="section">
            <h2 class="section-title">🏆 GitHub Trophies</h2>
            <div class="stat-card" style="margin-top: 2rem;">
                <img src="https://github-profile-trophy.vercel.app/?username=rabby005&theme=tokyonight&no-frame=true&no-bg=true&margin-w=4&column=4" alt="GitHub Trophies">
            </div>
        </section>
    </div>

    <script>
        // Typing animation
        const texts = ['Python Enthusiast', 'Web Developer', 'Problem Solver', 'Tech Explorer'];
        let textIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        const typingElement = document.getElementById('typing');

        function type() {
            const currentText = texts[textIndex];
            
            if (isDeleting) {
                typingElement.textContent = currentText.substring(0, charIndex - 1);
                charIndex--;
            } else {
                typingElement.textContent = currentText.substring(0, charIndex + 1);
                charIndex++;
            }

            if (!isDeleting && charIndex === currentText.length) {
                isDeleting = true;
                setTimeout(type, 2000);
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                textIndex = (textIndex + 1) % texts.length;
                setTimeout(type, 500);
            } else {
                setTimeout(type, isDeleting ? 50 : 100);
            }
        }

        type();

        // Scroll animation observer
        const sections = document.querySelectorAll('.section');
        
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, { threshold: 0.1 });

        sections.forEach(section => {
            observer.observe(section);
        });

        // Create floating particles
        function createParticles() {
            const hero = document.querySelector('.hero');
            for (let i = 0; i < 30; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.width = Math.random() * 5 + 2 + 'px';
                particle.style.height = particle.style.width;
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 6 + 's';
                particle.style.opacity = Math.random() * 0.5 + 0.2;
                hero.appendChild(particle);
            }
        }

        createParticles();

        // Smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                }
            });
        });
    </script>
</body>
</html>
