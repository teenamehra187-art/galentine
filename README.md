# 💖 Will You Be My Galentine?

An interactive, romantic web experience to ask someone to be your Galentine! This project is a beautifully designed single-page application with smooth animations, heartfelt memories, and a fun interactive "No" button that evades clicks.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Galentine? 💖</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <style>
        :root {
            --pink-primary: #FFADCB;
            --pink-dark: #FF85B3;
            --lavender: #D4C1EC;
            --cream: #FFF9FB;
            --text-color: #7A5C61;
        }

        body {
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--cream);
            color: var(--text-color);
            scroll-behavior: smooth;
        }

        /* Heart Frame Styling */
        .image-container {
            width: 100%;
            height: 200px;
            overflow: hidden;
            border-radius: 15px;
            border: 4px solid var(--pink-primary);
            box-shadow: 0 0 15px rgba(255, 133, 179, 0.3);
            margin-bottom: 15px;
            position: relative;
        }

        .memory-img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .memory-card:hover .memory-img {
            transform: scale(1.1);
        }

        /* Memories Carousel Layout */
        .carousel {
            display: flex;
            gap: 20px;
            overflow-x: auto;
            padding: 40px;
            scrollbar-width: none;
        }

        .memory-card {
            min-width: 280px;
            background: white;
            padding: 20px;
            border-radius: 25px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.05);
            text-align: center;
        }

        /* Buttons Section */
        .btn-container {
            position: relative;
            margin: 50px auto;
            width: 300px;
            height: 100px;
        }

        .btn {
            padding: 15px 40px;
            font-size: 1.2rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: 0.3s;
        }

        .yes-btn {
            background-color: var(--pink-dark);
            color: white;
            position: absolute;
            left: 20px;
            z-index: 10;
        }

        .no-btn {
            background-color: var(--lavender);
            color: var(--text-color);
            position: absolute;
            right: 20px;
        }

        /* Celebration Screen */
        #celebration {
            display: none;
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: var(--cream);
            z-index: 1000;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }
        
        section { min-height: 100vh; display: flex; flex-direction: column; align-items: center; justify-content: center; }
        h1 { color: var(--pink-dark); font-size: 2.5rem; }
    </style>
</head>
<body>

    <section>
        <h1>Hey Gal! ✨</h1>
        <p>Something special for you... Scroll down!</p>
    </section>

    <section id="memories">
        <h1>Our Best Memories 📸</h1>
        <div class="carousel">
            <div class="memory-card">
                <div class="image-container">
                    <img src="pic1.jpg" alt="Memory 1" class="memory-img"> </div>
                <span style="font-size: 2rem;">😂</span>
                <h3>Memorable Laughs</h3>
                <p>Humari woh crazy wali baatein!</p>
            </div>

            <div class="memory-card">
                <div class="image-container">
                    <img src="pic2.jpg" alt="Memory 2" class="memory-img"> </div>
                <span style="font-size: 2rem;">💖</span>
                <h3>Special Moment</h3>
                <p>Ye wala din humesha yaad rahega.</p>
            </div>
        </div>
    </section>

    <section>
        <h1>Will You Be My Galentine? 🎀</h1>
        <div class="btn-container">
            <button class="btn yes-btn" onclick="startCelebration()">YES!</button>
            <button class="btn no-btn" id="noBtn">No</button>
        </div>
    </section>

    <div id="celebration">
        <h1 style="font-size: 4rem;">YAYYY! 🎉</h1>
        <p style="font-size: 1.5rem;">I knew you'd say yes! 💖</p>
        <p><strong>When:</strong> Whenever you want jaanemann</p>
        <p><strong>Where:</strong> Our favorite spot</p>
        <button class="btn" style="background: var(--pink-primary); margin-top: 20px;" onclick="location.reload()">Reset</button>
    </div>

    <script>
        // No Button Runaway Logic
        const noBtn = document.getElementById('noBtn');
        noBtn.addEventListener('mouseover', () => {
            const x = Math.random() * (window.innerWidth - 150);
            const y = Math.random() * (window.innerHeight - 100);
            noBtn.style.position = 'fixed';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
        });

        // Confetti Celebration
        function startCelebration() {
            document.getElementById('celebration').style.display = 'flex';
            
            // Heart-shaped confetti logic
            var duration = 15 * 1000;
            var animationEnd = Date.now() + duration;
            var defaults = { startVelocity: 30, spread: 360, ticks: 60, zIndex: 0 };

            function randomInRange(min, max) {
              return Math.random() * (max - min) + min;
            }

            var interval = setInterval(function() {
              var timeLeft = animationEnd - Date.now();

              if (timeLeft <= 0) {
                return clearInterval(interval);
              }

              var particleCount = 50 * (timeLeft / duration);
              confetti(Object.assign({}, defaults, { particleCount, origin: { x: randomInRange(0.1, 0.3), y: Math.random() - 0.2 } }));
              confetti(Object.assign({}, defaults, { particleCount, origin: { x: randomInRange(0.7, 0.9), y: Math.random() - 0.2 } }));
            }, 250);
        }
    </script>
</body>
</html>

## ✨ Features

- **Landing Section** – A charming introduction with a call-to-action button
- **Memories Carousel** – Showcase your favorite moments or reasons why you cherish the friendship
- **Evasive "No" Button** – The "No" button escapes when hovered over (they can't escape! 😄)
- **Celebration Screen** – Confetti animation and a victory message when they click "YES"
- **Background Music** – Plays an instrumental as they explore (music toggle available)
- **Floating Hearts** – Ambient decorative hearts floating across the background
- **Responsive Design** – Works beautifully on mobile and desktop devices
- **Smooth Scrolling** – Navigate through sections with smooth scroll animations

## 🚀 Getting Started

### Prerequisites
- A modern web browser (Chrome, Firefox, Safari, Edge)
- A web server (for local testing) or simply open `index.html` in your browser

### Setup

1. **Clone or download** the project files
2. **Add your music** – Replace `song.mp3` with your own background music file in the root directory
3. **Customize the memories** – Edit the memory cards in `index.html` with your own messages
4. **Open in browser** – Open `index.html` directly or serve it via a local server

### To Run Locally
```bash
# Option 1: Python
python -m http.server 8000

# Option 2: Node.js (with http-server)
npx http-server

# Then navigate to http://localhost:8000
```

## 🎨 Customization

### Edit Memories
In `index.html`, find the memory cards section and modify the text and emojis:
```html
<div class="memory-card">
    <span class="emoji">😂</span>
    <h3>Your Title</h3>
    <p>Your custom message here</p>
</div>
```

### Change Colors
Modify the CSS variables in the `<style>` section:
```css
:root {
    --pink-primary: #FFADCB;
    --pink-dark: #FF85B3;
    --lavender: #D4C1EC;
    --cream: #FFF9FB;
    --text-color: #7A5C61;
}
```

### Update Music
Replace the source link in the audio tag:
```html
<audio id="bgMusic" loop>
    <source src="your-song.mp3" type="audio/mpeg">
</audio>
```

### Celebration Message
Find the celebration section and customize the message:
```html
<p><strong>When:</strong> Whenever you want jaanemann</p>
<p><strong>Where:</strong> Our favorite spot</p>
```

## 🎵 Music Note

The project includes a placeholder for background music (`song.mp3`). For the best experience:
- Use royalty-free music or a song you have permission to use
- MP3 format works best
- Host the file in the same directory as `index.html`

Some great sources:
- [Pixabay Music](https://pixabay.com/music/)
- [Freesound](https://freesound.org/)
- Your own music files

## 📱 Browser Compatibility

- ✅ Chrome/Chromium (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Edge (latest)
- ✅ Mobile browsers

## 📝 License

Feel free to use and customize this for your special someone! 💕

## 💬 Tips

- Personalize it! The more custom details, the more meaningful it becomes
- Test on the device your Galentine will use it on
- Make sure the music file is ready before sharing
- The evasive "No" button is just for fun – they'll want to click "YES"! ✨

---

Made with 💖 for asking that special person to be your Galentine!
