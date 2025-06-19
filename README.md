# metokim
[17:51, 19.6.2025] סאלי 2: ``html
<!DOCTYPE html>
<html lang="he">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>מתוקים באבן יהודה</title>
<style>
  body {
    font-family: Arial, sans-serif;
    direction: rtl;
    margin: 0; padding: 0;
    background: #fff0f5;
    display: flex;
    min-height: 100vh;
    flex-direction: column;
  }
  header {
    background: #ff69b4;
    color: white;
    padding: 20px;
    text-align: center;
    font-size: 28px;
    font-weight: bold;
  }
  #container {
    flex: 1;
    display: flex;
  }
  #sidebar {
    width: 150px;
    background: #f5c6d6;
    padding: 15px;
    box-sizing: border-box;
  }
  #sidebar button {
    width: 100%;
    margin-bottom: 10px;
    padding: 10px;
    border: none;
    background: #ff69b4;
    color: white;
    font-size: 18px;
    cursor: pointer;
    border-radius: 5px;
  }
  #sidebar button:hover {
    background: #d14c81;
  }
  #content {
    flex: 1;
    padding: 20px;
    box-sizing: border-box;
  }
  #search-bar {
    max-width: 400px;
    display: flex;
    margin-bottom: 20px;
  }
  #search-input {
    flex: 1;
    padding: 10px;
    font-size: 16px;
  }
  #search-button {
[17:51, 19.6.2025] סאלי 2: const btnOffers = document.getElementById('btn-offers');
    const homeSection = document.getElementById('home-section');
    const offersSection = document.getElementById('offers-section');

    btnHome.addEventListener('click', () => {
      homeSection.style.display = 'block';
      offersSection.style.display = 'none';
      btnHome.classList.add('active');
      btnOffers.classList.remove('active');
    });

    btnOffers.addEventListener('click', () => {
      homeSection.style.display = 'none';
      offersSection.style.display = 'block';
      btnOffers.classList.add('active');
      btnHome.classList.remove('active');
    });

    function updateDateTime() {
      const now = new Date();
      const options = { 
        year: 'numeric', month: 'numeric', day: 'numeric',
        hour: '2-digit', minute: '2-digit', second: '2-digit',
        hour12: false
      };
      document.getElementById('date-time').textContent = now.toLocaleString('he-IL', options);
    }
    setInterval(updateDateTime, 1000);
    updateDateTime();
  </script>
</body>
</html>
```

תגיד לי אם תרצה שאסביר איך לשמור ולהעלות!
[17:51, 19.6.2025] סאלי 2: padding: 10px 20px;
    background: #ff69b4;
    border: none;
    color: white;
    cursor: pointer;
  }
  .products {
    display: grid;
    grid-template-columns: repeat(auto-fill,minmax(250px,1fr));
    gap: 15px;
  }
  .product {
    background: white;
    border: 1px solid #ddd;
    padding: 15px;
    border-radius: 8px;
    text-align: center;
    box-shadow: 0 0 5px rgba(0,0,0,0.1);
  }
  .product img {
    max-width: 100%;
    height: 150px;
    object-fit: contain;
    background: white;
    border-radius: 8px;
  }
  .product h3 {
    margin: 10px 0 5px 0;
  }
  footer {
    background: #d14c81;
    color: white;
    text-align: center;
    padding: 10px 0;
    font-size: 16px;
  }
</style>
</head>
<body>
  <header>מתוקים באבן יהודה</header>
  <div id="container">
    <div id="sidebar">
      <button onclick="showPage('home')">דף הבית</button>
      <button onclick="showPage('offers')">מבצעים!</button>
    </div>
    <div id="content">
      <div id="home" class="page">
        <div id="search-bar">
          <input id="search-input" type="text" placeholder="חפש מוצר..." />
          <button id="search-button">חפש</button>
        </div>
        <div class="products" id="products-list">
          <div class="product" data-name="עוגיות שוקולד">
[17:51, 19.6.2025] סאלי 2: <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/69/Chocolate_Chip_Cookies_-_kimberlykv.jpg/320px-Chocolate_Chip_Cookies_-_kimberlykv.jpg" alt="עוגיות שוקולד" />
            <h3>עוגיות שוקולד</h3>
            <p>טעימות ומתוקות, מתאימות לכל אירוע.</p>
          </div>
          <div class="product" data-name="שוקו">
            <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Glass_of_Chocolate_Milkshake.jpg/320px-Glass_of_Chocolate_Milkshake.jpg" alt="שוקו" />
            <h3>שוקו</h3>
            <p>משקה שוקולד קר וטעים.</p>
          </div>
        </div>
      </div>
      <div id="offers" class="page" style="display:none;">
        <h2 style="color: blue;">מבצעים!</h2>
        <p>כאן תוכל למצוא את כל המבצעים החמים שלנו. בקרוב יתווספו מבצעים מיוחדים!</p>
        <button onclick="showPage('home')">חזרה לדף הבית</button>
      </div>
    </div>
  </div>
  <footer id="footer-date">טוען תאריך ושעה...</footer>

  <script>
    function showPage(pageId) {
      document.querySelectorAll('.page').forEach(page => {
        page.style.display = (page.id === pageId) ? 'block' : 'none';
      });
      if(pageId === 'home') {
        document.getElementById('search-input').value = '';
        filterProducts('');
      }
    }
[17:51, 19.6.2025] סאלי 2: const searchButton = document.getElementById('search-button');
    const searchInput = document.getElementById('search-input');
    const productsList = document.getElementById('products-list');

    searchButton.addEventListener('click', () => {
      const filter = searchInput.value.trim().toLowerCase();
      filterProducts(filter);
    });

    function filterProducts(filter) {
      const products = productsList.querySelectorAll('.product');
      products.forEach(product => {
        const name = product.getAttribute('data-name').toLowerCase();
        product.style.display = name.includes(filter) ? 'block' : 'none';
      });
    }

    function updateDateTime() {
      const now = new Date();
      const options = { 
        year: 'numeric', month: '2-digit', day: '2-digit',
        hour: '2-digit', minute: '2-digit', second: '2-digit',
        hour12: false 
      };
      const formatted = now.toLocaleDateString('he-IL', options).replace(/\//g, '-');
      document.getElementById('footer-date').textContent = formatted;
    }

    setInterval(updateDateTime, 1000);
    updateDateTime();
  </script>
</body>
</html>
```

---
