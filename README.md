<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Utsav Wraps | Celebrate Every Moment</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=Poppins:wght@300;400;500;600&display=swap" rel="stylesheet">

<style>

/* ---------- GLOBAL ---------- */
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:'Poppins',sans-serif;background:#faf7f2;color:#333;}
h1,h2,h3{font-family:'Playfair Display',serif;}
section{padding:70px 8%;}
button{cursor:pointer;border:none;}

/* ---------- NAVBAR ---------- */
nav{
display:flex;
justify-content:space-between;
align-items:center;
padding:20px 8%;
background:#fff;
position:sticky;
top:0;
z-index:1000;
box-shadow:0 2px 15px rgba(0,0,0,0.05);
}
.logo{font-size:24px;font-weight:700;color:#8b1e3f;}
nav ul{display:flex;gap:25px;list-style:none;}
nav ul li{cursor:pointer;font-weight:500;}
nav ul li:hover{color:#8b1e3f;}
.nav-icons{display:flex;gap:15px;}
.nav-icons button{
background:#8b1e3f;color:#fff;padding:8px 14px;border-radius:6px;
}

/* ---------- HERO ---------- */
.hero{
height:90vh;
background:linear-gradient(rgba(0,0,0,0.4),rgba(0,0,0,0.4)),
url('https://images.unsplash.com/photo-1607082348824-0a96f2a4b9da');
background-size:cover;
display:flex;
justify-content:center;
align-items:center;
flex-direction:column;
text-align:center;
color:#fff;
}
.hero h1{font-size:55px;margin-bottom:15px;}
.hero p{font-size:18px;margin-bottom:20px;}
.hero button{background:#fff;color:#8b1e3f;padding:12px 25px;border-radius:30px;font-weight:600;}

/* ---------- SEARCH ---------- */
.search-box{text-align:center;}
.search-box input{
width:60%;
padding:12px;
border:1px solid #ccc;
border-radius:30px;
}

/* ---------- PRODUCTS ---------- */
.products{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
gap:30px;
}
.card{
background:#fff;
border-radius:15px;
overflow:hidden;
box-shadow:0 5px 20px rgba(0,0,0,0.05);
transition:0.4s;
}
.card:hover{transform:translateY(-8px);}
.card img{width:100%;height:250px;object-fit:cover;}
.card-content{padding:20px;}
.price{color:#8b1e3f;font-weight:600;margin:8px 0;}
select{width:100%;padding:8px;margin:8px 0;}
.card button{
background:#8b1e3f;color:#fff;padding:10px;width:100%;border-radius:8px;
}

/* ---------- CART ---------- */
.cart-box{
background:#fff;
padding:25px;
border-radius:15px;
box-shadow:0 5px 15px rgba(0,0,0,0.05);
}
.cart-item{
display:flex;
justify-content:space-between;
margin-bottom:10px;
}
.total{font-weight:600;margin-top:10px;}

/* ---------- CHECKOUT ---------- */
.checkout input, .checkout select{
width:100%;
padding:10px;
margin:8px 0;
}
.checkout button{
background:#8b1e3f;color:#fff;padding:12px;border-radius:8px;width:100%;
}

/* ---------- ABOUT ---------- */
.about img{
width:100%;
max-width:500px;
border-radius:15px;
margin-top:20px;
}

/* ---------- CONTACT ---------- */
.contact{
background:#8b1e3f;
color:#fff;
text-align:center;
}

/* ---------- RESPONSIVE ---------- */
@media(max-width:768px){
.hero h1{font-size:32px;}
.search-box input{width:90%;}
}

</style>
</head>

<body>

<nav>
<div class="logo">Utsav Wraps</div>
<ul>
<li>Home</li>
<li>Collections</li>
<li>Wedding</li>
<li>Contact</li>
</ul>
<div class="nav-icons">
<button onclick="showCart()">Cart</button>
<button onclick="openLogin()">Login</button>
</div>
</nav>

<section class="hero">
<h1>Celebrate Every Moment</h1>
<p>Luxury Customized Potli Bags for Weddings & Festivals</p>
<button>Shop Now</button>
</section>

<section class="search-box">
<h2>Search Your Collection</h2>
<input type="text" id="search" placeholder="Karva Chauth, Diwali, Wedding..." onkeyup="searchProducts()">
</section>

<section class="products" id="productContainer">

<div class="card" data-name="wedding family bride groom">
<img src="https://images.unsplash.com/photo-1594737625785-a6cbdabd333c">
<div class="card-content">
<h3>Wedding Custom Potli</h3>
<p>Family Name / Bride & Groom Name Available</p>
<select onchange="updatePrice(this)">
<option value="149">Extra Small - ₹149</option>
<option value="249">Small - ₹249</option>
<option value="349">Medium - ₹349</option>
<option value="449">Extra Medium - ₹449</option>
</select>
<p class="price">₹149</p>
<button onclick="addToCart(this)">Add to Cart</button>
</div>
</div>

</section>

<section>
<h2>Your Cart</h2>
<div class="cart-box" id="cartBox"></div>
<p class="total" id="totalPrice">Total: ₹0</p>
</section>

<section class="checkout">
<h2>Checkout</h2>
<input placeholder="Full Name">
<input placeholder="Email">
<input placeholder="Mobile">
<input placeholder="Address">
<select>
<option>Cash on Delivery</option>
<option>UPI</option>
<option>Credit / Debit Card</option>
</select>
<button>Place Order</button>
</section>

<section class="about">
<h2>Our Story</h2>
<p>Utsav Wraps celebrates Indian traditions through premium handcrafted potli designs for weddings & festivals.</p>
<img src="YOUR_HISTORY_IMAGE.jpg">
</section>

<section class="contact">
<h2>Contact Us</h2>
<p>Email: hello@utsavwraps.in</p>
<p>Phone: +91 98765 43210</p>
<p>Address: Nagpur, Maharashtra, India</p>
</section>

<script>

let total = 0;

function updatePrice(select){
let price = select.value;
select.parentElement.querySelector(".price").innerText = "₹" + price;
}

function addToCart(btn){
let card = btn.parentElement;
let name = card.querySelector("h3").innerText;
let price = parseInt(card.querySelector("select").value);

let item = document.createElement("div");
item.classList.add("cart-item");
item.innerHTML = name + " - ₹" + price + 
" <button onclick='removeItem(this,"+price+")'>X</button>";

document.getElementById("cartBox").appendChild(item);

total += price;
document.getElementById("totalPrice").innerText = "Total: ₹" + total;
}

function removeItem(btn,price){
btn.parentElement.remove();
total -= price;
document.getElementById("totalPrice").innerText = "Total: ₹" + total;
}

function searchProducts(){
let input = document.getElementById("search").value.toLowerCase();
let cards = document.querySelectorAll(".card");

cards.forEach(card=>{
let name = card.getAttribute("data-name");
card.style.display = name.includes(input) ? "block" : "none";
});
}

</script>

</body>
</html>
