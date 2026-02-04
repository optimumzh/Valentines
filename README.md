<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine? 💕</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .container {
            text-align: center;
            background: white;
            padding: 60px 40px;
            border-radius: 30px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            max-width: 500px;
            width: 90%;
        }

        h1 {
            color: #ff6b9d;
            font-size: 2.5em;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        .heart {
            font-size: 4em;
            animation: heartbeat 1.5s ease-in-out infinite;
            margin: 20px 0;
        }

        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        .question {
            font-size: 1.5em;
            color: #333;
            margin-bottom: 40px;
        }

        .button-container {
            position: relative;
            display: flex;
            gap: 20px;
            justify-content: center;
            align-items: center;
            min-height: 60px;
        }

        button {
            padding: 15px 40px;
            font-size: 1.2em;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
            font-weight: bold;
        }

        #yesBtn {
            background: linear-gradient(135deg, #ff6b9d 0%, #ff8fab 100%);
            color: white;
        }

        #yesBtn:hover {
            transform: scale(1.1);
            box-shadow: 0 10px 30px rgba(255, 107, 157, 0.4);
        }

        #noBtn {
            background: linear-gradient(135deg, #a0a0a0 0%, #c0c0c0 100%);
            color: white;
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
        }

        #noBtn:hover {
            transform: translateX(-50%) scale(1.05);
        }

        .hearts-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .floating-heart {
            position: absolute;
            font-size: 2em;
            animation: float 6s ease-in-out infinite;
            opacity: 0.3;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(10deg); }
        }
    </style>
</head>
<body>
    <div class="hearts-background">
        <div class="floating-heart" style="left: 10%; top: 20%;">💖</div>
        <div class="floating-heart" style="left: 80%; top: 30%; animation-delay: 1s;">💕</div>
        <div class="floating-heart" style="left: 15%; top: 70%; animation-delay: 2s;">💗</div>
        <div class="floating-heart" style="left: 85%; top: 60%; animation-delay: 1.5s;">💝</div>
        <div class="floating-heart" style="left: 50%; top: 10%; animation-delay: 0.5s;">💓</div>
    </div>

    <div class="container">
        <h1>Will You Be My Valentine?</h1>
        <div class="heart">❤️</div>
        <p class="question">I have something important to ask you...</p>
        
        <div class="button-container">
            <button id="yesBtn">Yes! 💕</button>
            <button id="noBtn">No</button>
        </div>
    </div>

    <script>
        const noBtn = document.getElementById('noBtn');
        const yesBtn = document.getElementById('yesBtn');
        const container = document.querySelector('.button-container');

        // Function to move the No button away from the cursor
        function moveButton(e) {
            const btnRect = noBtn.getBoundingClientRect();
            const containerRect = container.getBoundingClientRect();
            
            // Calculate distance from cursor to button center
            const btnCenterX = btnRect.left + btnRect.width / 2;
            const btnCenterY = btnRect.top + btnRect.height / 2;
            const distanceX = e.clientX - btnCenterX;
            const distanceY = e.clientY - btnCenterY;
            const distance = Math.sqrt(distanceX * distanceX + distanceY * distanceY);
            
            // If cursor is within 150px of button, move it away
            if (distance < 150) {
                // Calculate new position (move away from cursor)
                const angle = Math.atan2(distanceY, distanceX);
                const moveDistance = 150 - distance + 50;
                
                let newX = btnCenterX - Math.cos(angle) * moveDistance - containerRect.left - btnRect.width / 2;
                let newY = btnCenterY - Math.sin(angle) * moveDistance - containerRect.top - btnRect.height / 2;
                
                // Keep button within reasonable bounds
                newX = Math.max(-100, Math.min(100, newX));
                newY = Math.max(-50, Math.min(50, newY));
                
                noBtn.style.left = `calc(50% + ${newX}px)`;
                noBtn.style.top = `${newY}px`;
            }
        }

        // Add mousemove listener to track cursor
        document.addEventListener('mousemove', moveButton);

        // Prevent the No button from being clicked
        noBtn.addEventListener('click', (e) => {
            e.preventDefault();
            // Make the button jump away when clicked
            const randomX = (Math.random() - 0.5) * 200;
            const randomY = (Math.random() - 0.5) * 100;
            noBtn.style.left = `calc(50% + ${randomX}px)`;
            noBtn.style.top = `${randomY}px`;
        });

        // Yes button redirects to the success page
        yesBtn.addEventListener('click', () => {
            window.location.href = 'yes.html';
        });
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yay! 💕</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .container {
            text-align: center;
            background: white;
            padding: 60px 40px;
            border-radius: 30px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            max-width: 600px;
            width: 90%;
            animation: slideIn 0.5s ease-out;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        h1 {
            color: #f5576c;
            font-size: 2.5em;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        .message {
            font-size: 1.3em;
            color: #333;
            margin-bottom: 30px;
            line-height: 1.6;
        }

        .gif-container {
            margin: 30px 0;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .gif-container img {
            width: 100%;
            max-width: 400px;
            display: block;
            margin: 0 auto;
        }

        .hearts {
            font-size: 3em;
            margin: 20px 0;
            animation: pulse 1s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }

        /* Confetti styles */
        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            background: #f5576c;
            position: absolute;
            animation: confetti-fall linear forwards;
        }

        @keyframes confetti-fall {
            to {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }

        canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 9999;
        }
    </style>
</head>
<body>
    <canvas id="confetti-canvas"></canvas>
    
    <div class="container">
        <h1>🎉 YAY! 🎉</h1>
        <div class="hearts">💕 ❤️ 💗 💖 💕</div>
        <p class="message">Thank you for saying yes to be my Valentine!</p>
        
        <div class="gif-container">
            <img src="https://media.tenor.com/o_5RQarGvJ0AAAAM/kiss.gif" alt="Happy Baby">
        </div>
        
        <p class="message">You just made me the happiest person! 🥰</p>
    </div>

    <script>
        // Confetti animation
        const canvas = document.getElementById('confetti-canvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const confettiColors = ['#ff6b9d', '#f5576c', '#f093fb', '#ffd700', '#ff69b4', '#ff1493', '#ff69b4'];
        const confettiPieces = [];
        const confettiCount = 150;

        class Confetti {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height - canvas.height;
                this.size = Math.random() * 8 + 5;
                this.speedY = Math.random() * 3 + 2;
                this.speedX = Math.random() * 2 - 1;
                this.color = confettiColors[Math.floor(Math.random() * confettiColors.length)];
                this.rotation = Math.random() * 360;
                this.rotationSpeed = Math.random() * 10 - 5;
            }

            update() {
                this.y += this.speedY;
                this.x += this.speedX;
                this.rotation += this.rotationSpeed;

                if (this.y > canvas.height) {
                    this.y = -10;
                    this.x = Math.random() * canvas.width;
                }
            }

            draw() {
                ctx.save();
                ctx.translate(this.x, this.y);
                ctx.rotate(this.rotation * Math.PI / 180);
                ctx.fillStyle = this.color;
                ctx.fillRect(-this.size / 2, -this.size / 2, this.size, this.size);
                ctx.restore();
            }
        }

        // Create confetti pieces
        for (let i = 0; i < confettiCount; i++) {
            confettiPieces.push(new Confetti());
        }

        // Animation loop
        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            confettiPieces.forEach(confetti => {
                confetti.update();
                confetti.draw();
            });

            requestAnimationFrame(animate);
        }

        animate();

        // Handle window resize
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
    </script>
</body>
</html>
