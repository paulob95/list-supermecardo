<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lista de Supermercado</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background-color: gray;
        text-align: center;
       
       
    }
    ul {
        list-style-type: none;
        padding: 0;
    }
    ul li {
        padding:10px;
        margin-bottom: 20px;
        background: #eee;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    button {
        cursor: pointer;
    }


img{      
   height:200px ;
   width: 200px;
   border-radius: 30px;

 }



</style>
</head>
<body>

<h2>Lista de Supermercado</h2>

<input type="text" id="product-name" placeholder="Nome do produto">
<input type="number" id="product-price" placeholder="Preço">
<button onclick="addProduct()">Adicionar Produto</button>

<ul id="product-list"></ul>

<p>Total: $<span id="total-price">0.00</span></p>

<br><br>





<a href="https://im.ge/i/images-removebg-preview-2.ZCY3SL"><img src="https://i.im.ge/2024/05/02/ZCY3SL.images-removebg-preview-2.th.png" alt="images removebg preview 2" border="0"></a>


               <h1>PH</h1>



<script>
let productList = [];
let totalPrice = 0;

function addProduct() {
    const productName = document.getElementById('product-name').value.trim();
    const productPrice = parseFloat(document.getElementById('product-price').value);
    if (productName !== "" && !isNaN(productPrice) && productPrice >= 0) {
        productList.push({ name: productName, price: productPrice });
        document.getElementById('product-name').value = '';
        document.getElementById('product-price').value = '';
        updateList();
    } else {
        alert("Por favor, insira um nome e preço válido para o produto.");
    }
}

function removeProduct(index) {
    productList.splice(index, 1);
    updateList();
}

function updateList() {
    const listElement = document.getElementById('product-list');
    listElement.innerHTML = '';
   
    totalPrice = 0;
    productList.forEach((product, index) => {
        const productElement = document.createElement('li');
        productElement.innerHTML = `
            ${product.name} - $${product.price.toFixed(2)}
            <button onclick="removeProduct(${index})">Excluir</button>
        `;
        listElement.appendChild(productElement);
       
        totalPrice += product.price;
    });
   
    document.getElementById('total-price').innerText = totalPrice.toFixed(2);
}

document.getElementById('product-name').addEventListener('keyup', function(event) {
    if (event.key === 'Enter') {
        addProduct();
    }
});

document.getElementById('product-price').addEventListener('keyup', function(event) {
    if (event.key === 'Enter') {
        addProduct();
    }
});
</script>

</body>
</html>
