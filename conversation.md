## カウントダウン終了時は黒字、ボールド、枠いっぱいの大きさにして

はい、カウントダウン終了時は黒字、ボールド、枠いっぱいの大きさになるように変更しました。

**変更点**

* カウントダウン終了時は黒字、ボールド、枠いっぱいの大きさ

**コード**

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Webアプリ</title>
  <style>
    body {
      font-family: sans-serif;
      margin: 20px;
    }
    .container {
      display: flex;
      justify-content: center;
    }
    .box {
      width: 100px;
      height: 100px;
      border: 1px solid #ccc;
      margin: 10px;
      text-align: center;
      line-height: 100px;
    }
    .button {
      margin: 10px;
      padding: 10px 20px;
      border: 1px solid #ccc;
      border-radius: 5px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="box">?</div>
    <div class="box">?</div>
    <div class="box">?</div>
  </div>
  <div class="container">
    <button class="button" id="start">スタート</button>
  </div>
  <script>
    const startButton = document.getElementById("start");
    const boxes = document.querySelectorAll(".box");
    let countdown = 3;
    const countdownElement = document.createElement("div");
    countdownElement.textContent = countdown;
    document.body.appendChild(countdownElement);

    startButton.addEventListener("click", () => {
      startButton.disabled = true;
      boxes.forEach((box) => {
        box.textContent = "?";
      });
      const intervalId = setInterval(() => {
        countdown -= 0.5;
        countdownElement.textContent = countdown.toFixed(1);
        if (countdown === 0) {
          clearInterval(intervalId);
          boxes.forEach((box) => {
            const alphabet = String.fromCharCode(
              Math.floor(Math.random() * 26) + 65
            );
            box.textContent = alphabet;
            box.style.fontSize = "100px";
            box.style.fontWeight = "bold";
            box.style.color = "black";
          });
          countdown = 3;
          startButton.disabled = false;
        } else {
          boxes.forEach((box) => {
            const alphabet = String.fromCharCode(
              Math.floor(Math.random() * 26) + 65
            );
            box.textContent = alphabet;
            box.style.fontSize = `${Math.floor(Math.random() * 20) + 10}px`;
            const colors = ["red", "green", "blue", "yellow", "purple"];
            box.style.color = colors[Math.floor(Math.random() * colors.length)];
          });
        }
      }, 500);
    });
  </script>
</body>
</html>
```

**動作**

1. ページを開くと、"スタート"ボタンと3つの"?"が表示されます。
2. "スタート"ボタンをクリックすると、カウントダウンが始まり、3つの箱の中身がランダムな文字に書き換わります。
3. 文字の大きさと色はランダムに変化します。
4. 3秒後に、3つの箱の中身がランダムなアルファベットに書き換わり、黒字、ボールド、枠いっぱいの大きさになります。
5. "スタート"ボタンをもう一度押すと、1から4までの動作が繰り返されます。

**補足**

* 上記のコードは基本的な動作のみを実装しています。
* デザインや機能は、必要に応じて追加・変更可能です。
* より詳細な情報は、Web開発に関する書籍やチュートリアルを参照してください。

**参考**

* HTML 入門: [[無効な URL を削除しました]]([無効な URL を削除しました])
* CSS 入門: [[無効な URL を削除しました]]([無効な URL

```
ソース:
1. https://sadaai.com/how-to-create-an-email-transmission-form-with-html/