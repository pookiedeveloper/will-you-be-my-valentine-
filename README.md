<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Valentine?</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: #ffffff; /* White background */
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            margin: 0;
            animation: backgroundAnim 5s ease-in-out infinite;
            background-color: #f8e0e0; /* Soft pink background */
        }

        @keyframes backgroundAnim {
            0% { background-color: #ffffff; }
            50% { background-color: #f0c7c7; }
            100% { background-color: #ffffff; }
        }

        h1 {
            color: #333333; /* Dark text color */
            margin-bottom: 30px;
            font-size: 36px;
        }

        .btn-container {
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
        }

        button {
            padding: 15px 30px;
            font-size: 18px;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease, background-color 0.5s ease;
            position: relative;
            z-index: 2;
        }

        #yesBtn {
            background-color: #28a745; /* Green button */
            color: white;
        }

        #noBtn {
            background-color: #dc3545; /* Red button */
            color: white;
            white-space: nowrap; /* Prevent text from breaking into new lines */
        }

        #yesBtn:hover {
            background-color: #218838; /* Darker green */
            transform: scale(1.1);
            box-shadow: 0 0 20px 5px rgba(40, 167, 69, 0.7);
        }

        #noBtn:hover {
            background-color: #c82333; /* Darker red */
            transform: scale(1.1);
            box-shadow: 0 0 20px 5px rgba(220, 53, 69, 0.7);
        }

        #cuteMessageContainer {
            position: absolute;
            top: -100px;
            text-align: center;
            display: none;
            animation: drop 1s ease forwards, bounce 1s ease-out;
        }

        @keyframes drop {
            to {
                top: 50%;
                transform: translateY(-50%);
            }
        }

        @keyframes bounce {
            0% { transform: translateY(-50px); }
            50% { transform: translateY(10px); }
            100% { transform: translateY(0); }
        }

        #cuteMessage {
            font-size: 32px;
            color: #28a745; /* Green text for the message */
            margin-bottom: 20px;
        }

        #valentineGif {
            width: 200px;
            margin-bottom: 20px;
        }

        #pandaGif {
            width: 250px;
            border-radius: 10px;
        }
    </style>
</head>
<body>

    <!-- Cute Valentine Gif -->
    <img id="valentineGif" src="https://media.giphy.com/media/3oriO0OEd9QIDdllqo/giphy.gif" alt="Cute Valentine Gif">

    <h1>Will You Be My Valentine?</h1>

    <div class="btn-container">
        <button id="yesBtn">Yes 🫣</button>
        <button id="noBtn">No</button>
    </div>

    <!-- Cute Message and Panda Gif -->
    <div id="cuteMessageContainer">
        <div id="cuteMessage">I KNEW YOU WOULD SAY YESS CUTIE 😘😚</div>
        <div id="cuteMessage2">MWAHH 😽</div>
        <img id="pandaGif" src="https://media.giphy.com/media/ArLxZ4PebH2Ug/giphy.gif" alt="Hugging Pandas">
    </div>

    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti"></script>

    <script>
        const yesBtn = document.getElementById('yesBtn');
        const noBtn = document.getElementById('noBtn');
        const cuteMessageContainer = document.getElementById('cuteMessageContainer');
        const cuteMessage2 = document.getElementById('cuteMessage2');

        let yesBtnSize = 1;
        let clickCount = 0;

        const noMessages = [
            "Are you sure? 😣",
            "Really? 😭",
            "Are you positive? 😟",
            "I will be very sad 😔",
            "Ahh, think about it!!!",
            "Please, pookiee! 😙",
            "Ahhh, I'll cry! 😭",
            "Why no? 😟",
            "Pleaseee babe! 😣",
            "Ohhh god 😟",
            "Why so 😔",
            "Fine, you left me no option 😙"
        ];

        const yesMessages = [
            "Yes 🫣",
            "Awww 🫣",  // Updated to Awww
            "I can cook 😋",
            "I can do the dishes also 😚",
            "Ahh, just say yesss 😭😭"
        ];

        noBtn.addEventListener('click', () => {
            // Increase Yes button size
            yesBtnSize += 0.3;
            yesBtn.style.transform = `scale(${yesBtnSize})`;

            // Update No button text based on click count
            if (clickCount < noMessages.length) {
                noBtn.textContent = noMessages[clickCount];
                clickCount++;
            }

            // Move No button slightly but keep it near Yes button
            noBtn.style.transform = `translate(${10 * clickCount}px, ${5 * clickCount}px)`;

            // Hide No button when Yes button covers the screen
            if (yesBtnSize >= 4) {
                noBtn.style.display = 'none';
            }

            // Update the Yes button text when red button is pressed
            if (clickCount <= yesMessages.length) {
                yesBtn.textContent = yesMessages[clickCount - 1];
            }
        });

        yesBtn.addEventListener('click', () => {
            // Directly show the final message
            document.querySelector('.btn-container').style.display = 'none';
            document.querySelector('h1').style.display = 'none';
            document.getElementById('valentineGif').style.display = 'none';
            cuteMessageContainer.style.display = 'block';

            // Confetti Animation
            confetti({
                particleCount: 100,
                spread: 70,
                origin: { x: 0.5, y: 0.5 }
            });

            // Personalized background change
            document.body.style.backgroundColor = "#f8e0e0"; /* Soft pink background */
        });
    </script>

</body>
</html>
