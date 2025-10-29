# singlepageapplicationn
!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Naan Mudhalvan Info SPA</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      font-family: 'Poppins', sans-serif;
      background: url('https://images.unsplash.com/photo-1499673610122-01c7122c5dcb?auto=format&fit=crop&w=1350&q=80') no-repeat center center fixed;
      background-size: cover;
      color: #fff;
      height: 100vh;
      overflow: hidden;
    }

    /* Transparent overlay moving background */
    .overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 200%;
      height: 200%;
      background: rgba(0, 0, 0, 0.4);
      animation: moveOverlay 20s linear infinite;
      pointer-events: none;
    }

    @keyframes moveOverlay {
      0% { transform: translate(0, 0); }
      50% { transform: translate(-25%, -25%); }
      100% { transform: translate(0, 0); }
    }

    header {
      position: relative;
      z-index: 10;
      padding: 20px 40px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: rgba(0, 0, 0, 0.6);
      backdrop-filter: blur(5px);
    }
    header h1 {
      font-size: 2rem;
    }

    nav a {
      color: #ffffffcc;
      margin-left: 20px;
      text-decoration: none;
      font-weight: 600;
      transition: color 0.3s;
      font-size: 1.1rem;
    }
    nav a:hover, nav a.active {
      color:palevioletred
    }

    main {
      position: relative;
      z-index: 10;
      max-width: 800px;
      margin: 40px auto;
      background: rgba(0,0,0,0.5);
      border: 3px solid pink;
      border-radius: 12px;
      padding: 30px;
      backdrop-filter: blur(10px);
      min-height: 300px;
      transition: opacity 0.4s ease;
    }

    img {
      width: 100%;
      border-radius: 8px;
      margin: 20px 0;
      border: 2px solid #fff;
    }

    h2 {
      margin-top: 0;
      color: #ffd700;
    }

    p, li {
      line-height: 1.6;
    }

    ul {
      list-style: disc inside;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <div class="overlay"></div>

  <header>
    <h1>Naan Mudhalvan</h1>
    <nav>
      <a href="#home" id="nav-home" class="active">Home</a>
      <a href="#about" id="nav-about">About</a>
      <a href="#gallery" id="nav-gallery">Gallery</a>
    </nav>
  </header>

  <main id="content">
    <!-- Dynamic content loads here -->
  </main>

  <script>
    const routes = {
      home: `
        <h2>Welcome to Naan Mudhalvan</h2>
        <p>The <strong>Naan Mudhalvan</strong> scheme is a flagship initiative launched by the Tamil Nadu government to empower youth by identifying and nurturing their talents, offering skill training, career guidance, and supporting them to face competitive exams and opportunities.</p>
        <img src="${"C:\Users\ADMIN\Pictures\image 2.png"}
      `,
      about: `
        <h2>About the Scheme</h2>
        <p>Under <strong>Naan Mudhalvan</strong>, students receive:</p>
        <ul>
          <li>Skill development training (soft skills, technical skills)</li>
          <li>Guidance on higher education and career pathways</li>
          <li>Support for competitive exams (coaching, study materials)</li>
          <li>Language training (English, regional, etc.)</li>
        </ul>
        <img src="${"C:\Users\ADMIN\Pictures\images.jpg"}
      `,
      gallery: `
        <h2>Gallery</h2>
        <p>Here are some images related to Naan Mudhalvan:</p>
        <img src="${"https://i.ytimg.com/vi/Zs4xCWHvD3U/maxresdefault.jpg"}" alt="Event Image 1">
        <img src="${"https://i.ytimg.com/vi/9wCvJXGjnNY/maxresdefault.jpg"}" alt="Event Image 2">
        <img src="${"https://i.ytimg.com/vi/vOuCs5r1G3A/maxresdefault.jpg"}" alt="Event Image 3">
        <img src="${"https://i.ytimg.com/vi/1015/600/350.jpg"}" alt="Related Image">
      `
    };

    const contentDiv = document.getElementById('content');
    const navLinks = document.querySelectorAll('nav a');

    function setActiveLink(hash) {
      navLinks.forEach(link => {
        if (link.getAttribute('href') === hash) {
          link.classList.add('active');
        } else {
          link.classList.remove('active');
        }
      });
    }

    function loadContent() {
      const hash = window.location.hash || '#home';
      const routeName = hash.substring(1);

      contentDiv.style.opacity = 0;
      setTimeout(() => {
        if (routes[routeName]) {
          contentDiv.innerHTML = routes[routeName];
        } else {
          contentDiv.innerHTML = `<h2>404 - Page Not Found</h2><p>Sorry, no content found.</p>`;
        }
        setActiveLink(hash);
        contentDiv.style.opacity = 1;
      }, 300);
    }

    window.addEventListener('hashchange', loadContent);
    loadContent(); // initial load
  </script>

</body>
</html>
