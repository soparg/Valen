<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Be My Valentine 💖</title>
  <style>
    /* General Styles */
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4); /* Romantic gradient */
      font-family: 'Pacifico', cursive;
      overflow: hidden;
      position: relative;
    }

    .container {
      text-align: center;
      z-index: 1;
    }

    h1 {
      color: #d63447; /* Romantic red */
      font-size: 4rem;
      margin-bottom: 20px;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
    }

    .buttons {
      margin-top: 20px;
    }

    button {
      padding: 15px 30px;
      font-size: 1.5rem;
      border: none;
      border-radius: 50px;
      cursor: pointer;
      margin: 0 10px;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }

    #yes {
      background-color: #ff69b4; /* Hot pink */
      color: white;
    }

    #yes:hover {
      background-color: #ff1493; /* Darker pink */
      transform: scale(1.1);
      box-shadow: 0 6px 8px rgba(0, 0, 0, 0.2);
    }

    #no {
      background-color: #f44336; /* Red */
      color: white;
      position: relative;
    }

    #no:hover {
      background-color: #d63447; /* Darker red */
      transform: scale(1.1);
      box-shadow: 0 6px 8px rgba(0, 0, 0, 0.2);
    }

    /* Heart Animation */
    .hearts {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 0;
    }

    .heart {
      position: absolute;
      color: #ff69b4; /* Hot pink */
      font-size: 24px;
      animation: float 6s infinite ease-in-out;
    }

    @keyframes float {
      0% {
        transform: translateY(100vh) rotate(0deg);
        opacity: 1;
      }
      100% {
        transform: translateY(-10vh) rotate(360deg);
        opacity: 0;
      }
    }

    /* Confetti Animation */
    .confetti {
      position: absolute;
      width: 10px;
      height: 10px;
      background-color: #ff69b4;
      animation: confetti-fall 3s linear infinite;
      z-index: 2;
    }

    @keyframes confetti-fall {
      0% {
        transform: translateY(-10vh) rotate(0deg);
      }
      100% {
        transform: translateY(100vh) rotate(360deg);
      }
    }
  </style>
  <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet"> <!-- Romantic font -->
</head>
<body>
  <div class="container">
    <h1>Will You Be My Valentine? 💖</h1>
    <div class="buttons">
      <button id="yes">Yes!</button>
      <button id="no">No</button>
    </div>
  </div>

  <!-- Heart animation -->
  <div class="hearts">
    <!-- Hearts will be dynamically generated here -->
  </div>

  <!-- Confetti container -->
  <div id="confetti-container">
    <!-- Confetti will be dynamically generated here -->
  </div>

  <script>
    const noButton = document.getElementById('no');
    const yesButton = document.getElementById('yes');
    const heartsContainer = document.querySelector('.hearts');
    const confettiContainer = document.getElementById('confetti-container');

    // Make the "No" button run away
    noButton.addEventListener('mouseover', () => {
      const x = Math.random() * (window.innerWidth - noButton.offsetWidth);
      const y = Math.random() * (window.innerHeight - noButton.offsetHeight);
      noButton.style.position = 'absolute';
      noButton.style.left = `${x}px`;
      noButton.style.top = `${y}px`;
    });

    // Custom message when "No" is clicked
    noButton.addEventListener('click', () => {
      alert("Aww, don't be shy! Give it another try! 😘");
    });

    // Redirect to Instagram profile when "Yes" is clicked
    yesButton.addEventListener('click', () => {
      alert("Yay! You made me the happiest! 💖");
      createConfetti();
      // Redirect to Instagram profile
      window.location.href = "https://www.instagram.com/someone.you.prob.know/";
    });

    // Create floating hearts
    function createHeart() {
      const heart = document.createElement('div');
      heart.classList.add('heart');
      heart.innerHTML = '❤️';
      heart.style.left = `${Math.random() * 100}vw`;
      heart.style.animationDuration = `${Math.random() * 4 + 2}s`;
      heartsContainer.appendChild(heart);

      // Remove heart after animation ends
      setTimeout(() => {
        heart.remove();
      }, 6000);
    }

    // Generate hearts every 300ms
    setInterval(createHeart, 300);

    // Create confetti
    function createConfetti() {
      for (let i = 0; i < 100; i++) {
        const confetti = document.createElement('div');
        confetti.classList.add('confetti');
        confetti.style.left = `${Math.random() * 100}vw`;
        confetti.style.backgroundColor = `hsl(${Math.random() * 360}, 100%, 75%)`;
        confetti.style.animationDuration = `${Math.random() * 2 + 1}s`;
        confettiContainer.appendChild(confetti);

        // Remove confetti after animation ends
        setTimeout(() => {
          confetti.remove();
        }, 3000);
      }
    }
  </script>
</body>
</html>
