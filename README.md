<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Votação - Influencers Xanxerê</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: url('https://i.pinimg.com/originals/77/ce/9e/77ce9e8c915e6b1c54988e22b65b5a64.jpg') no-repeat center center/cover;
            text-align: center;
            color: white;
        }
        .login-container {
            width: 300px;
            margin: 100px auto;
            padding: 20px;
            background: #fff;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
            text-align: center;
        }
        .login-container h2 {
            color: black;
        }
        .login-container img {
            width: 50px;
            margin-bottom: 10px;
        }
        .login-container input {
            width: calc(100% - 20px);
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
            display: block;
        }
        .login-container button {
            width: 100%;
            padding: 10px;
            background: #0078D7;
            border: none;
            color: white;
            font-size: 16px;
            border-radius: 5px;
            cursor: pointer;
        }
        .login-container button:hover {
            background: #005bb5;
        }
        .influencer img {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            object-fit: cover;
        }
        .admin-container {
            display: none;
            width: 80%;
            margin: 50px auto;
            padding: 20px;
            background: #fff;
            color: black;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
        }
        .popup {
            display: none;
            position: fixed;
            bottom: 10px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0, 0, 0, 0.8);
            color: white;
            padding: 10px;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div id="login-container" class="login-container">
        <img src="https://cdn-icons-png.flaticon.com/512/174/174855.png" alt="Instagram">
        <h2>Faça login</h2>
        <input type="text" id="username" placeholder="Usuário">
        <input type="password" id="password" placeholder="Senha">
        <button onclick="login()">Conectar</button>
    </div>
    
    <div id="voting-container" class="container" style="display: none;">
        <button onclick="toggleMenu()">Menu</button>
        <div class="menu-overlay" id="menu-overlay">
            <button onclick="logout()">Sair</button>
            <button onclick="window.location.href='informacoes.html'">Mais Informações</button>
        </div>
        <h1>Vote na sua Influencer Favorita!</h1>
        <div class="influencer">
            <img src="https://64.media.tumblr.com/d8d0e7eef40226dfb75aaec960f6ab8e/37f3a2cf5c62451b-56/s1280x1920/8c9d4a47aa6be2b52dd009a4cfeedcf379254aa8.jpg" alt="Mariana">
            <p>Mariana</p>
            <button onclick="vote('Mariana')">Votar</button>
        </div>
        <div class="influencer">
            <img src="https://1.bp.blogspot.com/-1AZbBDi5nZQ/WKnmPH7zYzI/AAAAAAAAKgA/08oT5TiJI2QxUEXW9PrDzBk5BO6I9FUYgCLcB/s1600/cacau-lemos-blog-do-heroi.jpg" alt="Evylin">
            <p>Evylin</p>
            <button onclick="vote('Evylin')">Votar</button>
        </div>
        <div class="influencer">
            <img src="https://i.imgur.com/Z0uXucz.jpeg" alt="Laura">
            <p>Laura</p>
            <button onclick="vote('Laura')">Votar</button>
        </div>
    </div>

    <div id="admin-container" class="admin-container">
        <h2>Lista de Votos</h2>
        <ul id="vote-list"></ul>
    </div>

    <div id="popup" class="popup">Conta deslogada com sucesso</div>

    <script>
        let hasVoted = false;
        let loggedIn = false;
        let votes = [];

        function login() {
            let username = document.getElementById('username').value;
            let password = document.getElementById('password').value;
            
            if (username === "adm01" && password === "gugama3110") {
                document.getElementById('login-container').style.display = 'none';
                document.getElementById('admin-container').style.display = 'block';
                displayVotes();
                return;
            }
            
            if (username && password) {
                loggedIn = true;
                document.getElementById('login-container').style.display = 'none';
                document.getElementById('voting-container').style.display = 'block';
            } else {
                alert('Preencha todos os campos!');
            }
        }

        function vote(candidate) {
            if (hasVoted) {
                alert('Você já votou!');
                return;
            }
            votes.push({ username: document.getElementById('username').value, candidate });
            hasVoted = true;
            alert('Voto computado com sucesso!');
        }

        function displayVotes() {
            let voteList = document.getElementById('vote-list');
            voteList.innerHTML = votes.map(vote => `<li>${vote.username} votou em ${vote.candidate}</li>`).join('');
        }
    </script>
</body>
</html>
