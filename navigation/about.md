---
layout: post
title: About
permalink: /about/
comments: true
---

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Confetti Fun!</title>
  <style>
    /* Confetti canvas stays in the background */
    #confetti-canvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1;
    }

    /* Centered message styling */
    .center-message {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      z-index: 2;
      text-align: center;
      font-family: 'Segoe UI', sans-serif;
      color: #222;
      font-size: 3rem;
      font-weight: bold;
      background: linear-gradient(90deg, #ff6ec4, #7873f5);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
  </style>
</head>
<body>
  <!-- Confetti canvas -->
  <canvas id="confetti-canvas"></canvas>

  <!-- Cool center message -->
  <div class="center-message">
    Welcome!!
  </div>

  <!-- Confetti script -->
  <script>
    const canvas = document.getElementById('confetti-canvas');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    window.addEventListener('resize', () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    });

    const confetti = [];
    const confettiCount = 150;
    const colors = ['#f94144', '#f3722c', '#f9c74f', '#43aa8b', '#577590', '#9b5de5'];

    for (let i = 0; i < confettiCount; i++) {
      confetti.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height - canvas.height,
        r: Math.random() * 6 + 4,
        d: Math.random() * confettiCount,
        color: colors[Math.floor(Math.random() * colors.length)],
        tilt: Math.floor(Math.random() * 10) - 10,
        tiltAngleIncremental: (Math.random() * 0.07) + 0.05,
        tiltAngle: 0
      });
    }

    function drawConfetti() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      confetti.forEach((c, index) => {
        ctx.beginPath();
        ctx.lineWidth = c.r;
        ctx.strokeStyle = c.color;
        ctx.moveTo(c.x + c.tilt + (c.r / 2), c.y);
        ctx.lineTo(c.x + c.tilt, c.y + c.tilt + (c.r / 2));
        ctx.stroke();
      });

      updateConfetti();
    }

    function updateConfetti() {
      confetti.forEach((c, i) => {
        c.tiltAngle += c.tiltAngleIncremental;
        c.y += (Math.cos(c.d) + 3 + c.r / 2) / 2;
        c.x += Math.sin(0);
        c.tilt = Math.sin(c.tiltAngle) * 15;

        if (c.y > canvas.height) {
          confetti[i] = {
            x: Math.random() * canvas.width,
            y: -20,
            r: c.r,
            d: c.d,
            color: c.color,
            tilt: c.tilt,
            tiltAngleIncremental: c.tiltAngleIncremental,
            tiltAngle: c.tiltAngle
          };
        }
      });
    }

    (function loop() {
      requestAnimationFrame(loop);
      drawConfetti();
    })();
  </script>
</body>
</html>


## Hello, My name is Virginia or Ginny and here is a bit about me!


<style>
    /* Style looks pretty compact, 
       - grid-container and grid-item are referenced the code 
    */
    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Dynamic columns */
        gap: 10px;
    }
    .grid-item {
        text-align: center;
    }
    .grid-item img {
        width: 100%;
        height: 100px; /* Fixed height for uniformity */
        object-fit: contain; /* Ensure the image fits within the fixed height */
    }
    .grid-item p {
        margin: 5px 0; /* Add some margin for spacing */
    }

    .image-gallery {
        display: flex;
        flex-wrap: nowrap;
        overflow-x: auto;
        gap: 10px;
        }

    .image-gallery img {
        max-height: 150px;
        object-fit: cover;
        border-radius: 5px;
    }
</style>

<!-- This grid_container class is used by CSS styling and the id is used by JavaScript connection -->
<div class="grid-container" id="grid_container">
    <!-- content will be added here by JavaScript -->
</div>

<script>
    // 1. Make a connection to the HTML container defined in the HTML div
    var container = document.getElementById("grid_container"); // This container connects to the HTML div

    // 2. Define a JavaScript object for our http source and our data rows for the Living in the World grid
    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
        
    ];

    // 3a. Consider how to update style count for size of container
    // The grid-template-columns has been defined as dynamic with auto-fill and minmax

    // 3b. Build grid items inside of our container for each row of data
    for (const location of living_in_the_world) {
        // Create a "div" with "class grid-item" for each row
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";  // This class name connects the gridItem to the CSS style elements
        // Add "img" HTML tag for the flag
        var img = document.createElement("img");
        img.src = http_source + location.flag; // concatenate the source and flag
        img.alt = location.flag + " Flag"; // add alt text for accessibility

        // Add "p" HTML tag for the description
        var description = document.createElement("p");
        description.textContent = location.description; // extract the description

        // Add "p" HTML tag for the greeting
        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;  // extract the greeting

        // Append img and p HTML tags to the grid item DIV
        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);

        // Append the grid item DIV to the container DIV
        container.appendChild(gridItem);
    }
</script>

### Some things about me!

- I love to swim 🏊! I am on the school swim team
- I have been playing piano since I was five years old 🎹
- I am very passionate about STEM! My academic interests are math 🧮, computer science 💻, and astrophysics 🪐. 
- I am a part of CyberPatriot and won nationals last year with my team!
- I am the Director of Social Media at All Girls STEM Society, where we work to inspire young girls to see a future in STEM. 💗
- I also love trying new food! My favorite restaurant is Seven Grams or Din Tai Fung. 🥟
- Traveling is something I also enjoy. One day I want to travel the ENTIRE WORLDDD 🌏✈️
- 🎶 Listening to music is something I do quite often! I listen to mostly RnB, my favorite artists are Daniel Ceasar, Brent Faiyaz, Steve Lacy, SZA! 

### This summer I went to UCSD COSMOS! I learned lots of coding and made a color recognition robot monkey to win first overall in the final project.

<comment>
Here are some pictures!!
<comment>

<div class="image-gallery">
  <img src="{{site.baseurl}}/images/about/cosmos.png" alt="Image 1">
  <img src="{{site.baseurl}}/images/about/IMG_9801.png" alt="Image 2">
  <img src="{{site.baseurl}}/images/about/IMG_1552.png" alt="Image 3">
  <img src="{{site.baseurl}}/images/about/IMG_6397.png" alt="Image 4">
  <img src="{{site.baseurl}}/images/about/IMG_6465.png" alt="Image 5">
  <img src="{{site.baseurl}}/images/about/IMG_6449.png" alt="Image 6">
  <img src="{{site.baseurl}}/images/about/IMG_6476.png" alt="Image 7">
  <img src="{{site.baseurl}}/images/about/IMG_6526.png" alt="Image 8">
</div>
