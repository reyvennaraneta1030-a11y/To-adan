
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Happy Birthday Dan!</title>

<style>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    body {
        height: 100vh;
        overflow: hidden;
        font-family: Georgia, serif;
        background: linear-gradient(135deg, #ffd6e0, #fff0f3);
        display: flex;
        justify-content: center;
        align-items: center;
    }

    /* Background sparkles */
    .sparkle {
        position: fixed;
        color: white;
        font-size: 20px;
        animation: sparkle 3s infinite ease-in-out;
        pointer-events: none;
    }

    .s1 { top: 15%; left: 15%; }
    .s2 { top: 25%; right: 15%; animation-delay: 1s; }
    .s3 { bottom: 20%; left: 25%; animation-delay: 2s; }
    .s4 { bottom: 15%; right: 25%; animation-delay: .5s; }

    @keyframes sparkle {
        0%, 100% {
            opacity: .2;
            transform: scale(.7);
        }
        50% {
            opacity: 1;
            transform: scale(1.3);
        }
    }

    /* Letter */
    .letter {
        width: 320px;
        height: 220px;
        position: relative;
        cursor: pointer;
        transition: transform .4s;
    }

    .letter:hover {
        transform: scale(1.03);
    }

    .envelope {
        width: 100%;
        height: 100%;
        background: #fff8ed;
        border-radius: 10px;
        position: absolute;
        box-shadow: 0 15px 35px rgba(100, 40, 50, .2);
        overflow: hidden;
    }

    /* Envelope bottom folds */
    .envelope:before {
        content: "";
        position: absolute;
        bottom: 0;
        left: 0;
        border-left: 160px solid transparent;
        border-right: 160px solid transparent;
        border-bottom: 120px solid #f3c8b8;
        z-index: 2;
    }

    .envelope:after {
        content: "";
        position: absolute;
        bottom: 0;
        left: 0;
        border-left: 160px solid #f8d8ca;
        border-top: 110px solid transparent;
        z-index: 3;
    }

    /* Flap */
    .flap {
        position: absolute;
        top: 0;
        left: 0;
        width: 0;
        height: 0;
        border-left: 160px solid transparent;
        border-right: 160px solid transparent;
        border-top: 120px solid #eeb5a5;
        z-index: 5;
        transform-origin: top;
        transition: transform 1s;
    }

    /* Heart seal */
    .seal {
        position: absolute;
        top: 88px;
        left: 50%;
        transform: translateX(-50%);
        z-index: 10;
        font-size: 35px;
        transition: opacity .5s;
    }

    .tap-text {
        position: absolute;
        bottom: -55px;
        width: 100%;
        text-align: center;
        color: #8c4050;
        font-size: 17px;
        animation: bounce 1.5s infinite;
    }

    @keyframes bounce {
        0%, 100% { transform: translateY(0); }
        50% { transform: translateY(-7px); }
    }

    /* Popup */
    .popup {
        position: fixed;
        inset: 0;
        background: rgba(70, 20, 35, .45);
        backdrop-filter: blur(5px);
        display: flex;
        justify-content: center;
        align-items: center;
        opacity: 0;
        visibility: hidden;
        transition: .5s;
        z-index: 100;
    }

    .popup.active {
        opacity: 1;
        visibility: visible;
    }

    .message {
        width: 90%;
        max-width: 430px;
        max-height: 90vh;
        overflow-y: auto;
        background: #fffaf7;
        border-radius: 25px;
        padding: 30px 25px;
        text-align: center;
        box-shadow: 0 20px 50px rgba(0,0,0,.25);
        transform: scale(.7);
        transition: .5s;
    }

    .popup.active .message {
        transform: scale(1);
    }

    .message h1 {
        color: #b83250;
        font-size: 32px;
        margin-bottom: 12px;
    }

    .message p {
        color: #5e4147;
        font-size: 17px;
        line-height: 1.6;
    }

    .close {
        margin-top: 20px;
        border: none;
        background: #c84b67;
        color: white;
        padding: 10px 25px;
        border-radius: 25px;
        font-size: 16px;
        cursor: pointer;
    }

    .close:hover {
        background: #a93651;
    }

    /* =====================
       DIGITAL ROSE
       ===================== */

    .rose-container {
        height: 210px;
        display: flex;
        justify-content: center;
        align-items: flex-end;
        position: relative;
        margin: 10px 0;
    }

    .stem {
        width: 9px;
        height: 115px;
        background: linear-gradient(to right, #267344, #55a65f);
        border-radius: 10px;
        position: absolute;
        bottom: 10px;
        left: 50%;
        transform: translateX(-50%);
    }

    .leaf {
        width: 55px;
        height: 25px;
        background: #3c914d;
        border-radius: 100% 0 100% 0;
        position: absolute;
    }

    .leaf.left {
        left: 30%;
        bottom: 65px;
        transform: rotate(25deg);
    }

    .leaf.right {
        right: 30%;
        bottom: 90px;
        transform: rotate(155deg);
    }

    .rose {
        position: absolute;
        bottom: 105px;
        left: 50%;
        width: 100px;
        height: 100px;
        transform: translateX(-50%);
        animation: roseFloat 3s ease-in-out infinite;
    }

    .petal {
        position: absolute;
        width: 55px;
        height: 55px;
        background: linear-gradient(135deg, #ff416c, #b8123e);
        border-radius: 50% 50% 45% 45%;
        box-shadow: inset -5px -5px 10px rgba(100,0,30,.25);
    }

    .p1 {
        left: 23px;
        top: 5px;
    }

    .p2 {
        left: 5px;
        top: 25px;
        transform: rotate(-35deg);
    }

    .p3 {
        right: 5px;
        top: 25px;
        transform: rotate(35deg);
    }

    .p4 {
        left: 20px;
        bottom: 3px;
        transform: rotate(15deg);
    }

    .p5 {
        right: 20px;
        bottom: 3px;
        transform: rotate(-15deg);
    }

    .center {
        position: absolute;
        width: 48px;
        height: 48px;
        background: radial-gradient(circle at 35% 35%, #ff6684, #a30e38);
        border-radius: 50%;
        top: 27px;
        left: 26px;
        z-index: 5;
        box-shadow: inset -5px -5px 8px rgba(80,0,20,.3);
    }

    @keyframes roseFloat {
        0%, 100% {
            transform: translateX(-50%) rotate(-2deg);
        }
        50% {
            transform: translateX(-50%) rotate(2deg) translateY(-6px);
        }
    }

    .petal,
    .center {
        animation: bloom 1.5s ease-out forwards;
    }

    @keyframes bloom {
        from {
            transform: scale(0);
            opacity: 0;
        }
        to {
            opacity: 1;
        }
    }

    /* Falling hearts */
    .heart {
        position: fixed;
        top: -20px;
        color: #e84a6b;
        animation: fall 5s linear infinite;
        pointer-events: none;
        z-index: 150;
    }

    @keyframes fall {
        to {
            transform: translateY(110vh) rotate(360deg);
            opacity: 0;
        }
    }
</style>
</head>

<body>

<div class="sparkle s1">✦</div>
<div class="sparkle s2">✧</div>
<div class="sparkle s3">✦</div>
<div class="sparkle s4">✧</div>

<!-- LETTER -->
<div class="letter" onclick="openLetter()">

    <div class="envelope"></div>

    <div class="flap" id="flap"></div>

    <div class="seal" id="seal">💗</div>

    <div class="tap-text">
        Tap the letter 💌
    </div>

</div>


<!-- POPUP MESSAGE -->
<div class="popup" id="popup">

    <div class="message">

        <h1>🎉 Happy Birthday Dan! 🎂</h1>

        <!-- Digital Rose -->
        <div class="rose-container">

            <div class="stem"></div>

            <div class="leaf left"></div>
            <div class="leaf right"></div>

            <div class="rose">
                <div class="petal p1"></div>
                <div class="petal p2"></div>
                <div class="petal p3"></div>
                <div class="petal p4"></div>
                <div class="petal p5"></div>
                <div class="center"></div>
            </div>

        </div>

        <p>
            Happy Birthday, Dan! 🎈
            <br><br>

            I hope your special day is filled with
            happiness, laughter, and unforgettable
            moments. May this new year of your life
            bring you many amazing experiences,
            good memories, and reasons to smile.
            
            <br><br>

            sorry kung Dili ko ka adto hehhe lab lab reyvenn 🌹✨
            <br><br>

            <b>Happy Birthday once again, Dan! 💖</b>
        </p>

        <button class="close" onclick="closeLetter()">
            Close 💌
        </button>

    </div>

</div>


<script>

function openLetter() {

    document.getElementById("flap").style.transform =
        "rotateX(180deg)";

    document.getElementById("seal").style.opacity = "0";

    setTimeout(function() {
        document.getElementById("popup").classList.add("active");
        createHearts();
    }, 700);
}


function closeLetter() {

    document.getElementById("popup").classList.remove("active");

    setTimeout(function() {

        document.getElementById("flap").style.transform =
            "rotateX(0deg)";

        document.getElementById("seal").style.opacity = "1";

    }, 400);
}


/* Create falling hearts */
function createHearts() {

    for (let i = 0; i < 18; i++) {

        let heart = document.createElement("div");

        heart.className = "heart";
        heart.innerHTML = "♥";

        heart.style.left = Math.random() * 100 + "vw";
        heart.style.fontSize =
            (12 + Math.random() * 18) + "px";

        heart.style.animationDelay =
            Math.random() * 4 + "s";

        document.body.appendChild(heart);

        setTimeout(() => {
            heart.remove();
        }, 9000);
    }
}


/* Close popup by pressing Escape */
document.addEventListener("keydown", function(event) {

    if (event.key === "Escape") {
        closeLetter();
    }

});

</script>

</body>
</html>
