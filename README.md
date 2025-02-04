<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Caça ao Tesouro</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }
        #pista-container {
            display: none;
            margin-top: 20px;
            animation: fadeIn 1s;
        }
        input {
            padding: 10px;
            width: 300px;
            margin-top: 10px;
        }
        button {
            padding: 10px 15px;
            cursor: pointer;
            margin-top: 10px;
        }
        #mensagem {
            margin-top: 20px;
            font-weight: bold;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>
    <h1>Bem-vinda à Caça ao Tesouro!</h1>
    <p>Resolva as charadas para encontrar o presente final. Insira a resposta correta para receber a localização do QR Code com a próxima pista.</p>
    
    <div id="pista-container">
        <h2 id="pista"></h2>
        <input type="text" id="resposta" placeholder="Digite sua resposta">
        <button onclick="verificarResposta()">Enviar</button>
        <p id="mensagem"></p>
    </div>
    
    <button onclick="iniciarJogo()">Iniciar Jogo</button>
    
    <script>
        const pistas = [
            {
                charada: "Ele foi o homem que sonhou e construiu. No coração da cidade, sua presença ainda se faz sentir. Seu olhar repousa sobre aqueles que passam. Onde ele está?",
                resposta: "praça cívica",
                proximaPista: "Parabéns! Vá até a Praça Cívica e procure um QR Code próximo à estátua de Pedro Ludovico para a próxima charada!",
                qrCode: "https://www.exemplo.com/qr1.png"
            },
            {
                charada: "As paredes aqui guardam segredos de um tempo passado, mas ainda contam histórias do presente. Aqui viveu um homem cuja assinatura moldou a cidade. Onde estou?",
                resposta: "museu pedro ludovico",
                proximaPista: "Ótimo! Vá até o Museu Pedro Ludovico e encontre um QR Code próximo à entrada principal!",
                qrCode: "https://www.exemplo.com/qr2.png"
            },
            {
                charada: "Em meio ao verde, onde a água descansa e os pássaros cantam, existe um lugar onde a natureza encontra a arte. Venha, respire fundo e encontre o caminho. Onde estou?",
                resposta: "bosque dos buritis",
                proximaPista: "Incrível! Agora siga até o Bosque dos Buritis e escaneie o QR Code próximo ao lago!",
                qrCode: "https://www.exemplo.com/qr3.png"
            },
            {
                charada: "Linhas que desafiam a gravidade, curvas que contam histórias de um mestre do concreto. Aqui, a arquitetura dança com a cultura. Onde estou?",
                resposta: "centro cultural oscar niemeyer",
                proximaPista: "Você está indo muito bem! Vá até o Centro Cultural Oscar Niemeyer e encontre um QR Code próximo ao prédio principal.",
                qrCode: "https://www.exemplo.com/qr4.png"
            },
            {
                charada: "Grandes espelhos d'água refletem o céu. As famílias vêm aqui para celebrar, os amantes para caminhar, e os sonhos para se realizar. Onde estou?",
                resposta: "parque flamboyant",
                proximaPista: "Última etapa! Vá até o Parque Flamboyant e procure um QR Code próximo ao lago!",
                qrCode: "https://www.exemplo.com/qr5.png"
            }
        ];
        
        let indiceAtual = 0;
        
        function iniciarJogo() {
            document.getElementById("pista-container").style.display = "block";
            document.getElementById("pista").textContent = pistas[indiceAtual].charada;
        }
        
        function verificarResposta() {
            let resposta = document.getElementById("resposta").value.toLowerCase().trim();
            if (resposta === pistas[indiceAtual].resposta) {
                document.getElementById("mensagem").textContent = pistas[indiceAtual].proximaPista;
                document.getElementById("mensagem").innerHTML += `<br><img src="${pistas[indiceAtual].qrCode}" alt="QR Code" style="max-width: 200px;">`;
                indiceAtual++;
                if (indiceAtual < pistas.length) {
                    setTimeout(() => {
                        document.getElementById("pista").textContent = pistas[indiceAtual].charada;
                        document.getElementById("mensagem").textContent = "";
                        document.getElementById("resposta").value = "";
                    }, 3000);
                } else {
                    document.getElementById("mensagem").textContent = "Parabéns! Você completou a caça ao tesouro e encontrou seu presente!";
                }
            } else {
                document.getElementById("mensagem").textContent = "Resposta incorreta. Tente novamente!";
            }
        }
    </script>
</body>
</html>
