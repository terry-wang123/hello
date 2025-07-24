Hey bro
<head>
  <meta charset="UTF-8">
  <title>多首歌播放器</title>
  <style>
    body {
      font-family: "微軟正黑體", sans-serif;
      background-color: #f0f0f0;
      text-align: center;
      padding: 40px;
    }

    h1 {
      color: #333;
    }

    #playlist {
      list-style: none;
      padding: 0;
    }

    #playlist li {
      padding: 10px;
      cursor: pointer;
      color: #0066cc;
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <title>自動播放清單</title>
  <style>
    body {
      font-family: "微軟正黑體", sans-serif;
      background-color: #f7f7f7;
      text-align: center;
      padding: 40px;
    }

    h1 {
      color: #222;
    }

    audio {
      margin-top: 20px;
      width: 300px;
    }

    ul {
      list-style: none;
      padding: 0;
      max-width: 300px;
      margin: 20px auto;
    }

    li {
      padding: 10px;
      border-bottom: 1px solid #ccc;
      cursor: pointer;
      color: #0066cc;
    }

    li:hover {
      background-color: #eee;
    }

    li.active {
      font-weight: bold;
      color: red;
    }
  </style>
</head>
<body>

  <h1>🎵 自動播放音樂清單</h1>

  <audio id="player" controls>
    <source src="music1.mp3" type="audio/mpeg">
    你的瀏覽器不支援音樂播放。
  </audio>

  <ul id="playlist">
    <li data-src="music.mp3" class="active">🎶 歌曲 1</li>
    <li data-src="music1.mp3">🎶 歌曲 2</li>
    <li data-src="music2.mp3">🎶 歌曲 3</li>
    <li data-src="music3.mp3">🎶 歌曲 3</li>
  </ul>

  <script>
    const audio = document.getElementById("player");
    const listItems = document.querySelectorAll("#playlist li");
    let currentIndex = 0;

    function playSong(index) {
      listItems.forEach(li => li.classList.remove("active"));
      const selected = listItems[index];
      selected.classList.add("active");
      audio.src = selected.getAttribute("data-src");
      audio.play();
      currentIndex = index;
    }

    listItems.forEach((item, index) => {
      item.addEventListener("click", () => playSong(index));
    });

    // 自動播放下一首
    audio.addEventListener("ended", () => {
      let nextIndex = currentIndex + 1;
      if (nextIndex >= listItems.length) {
        nextIndex = 0; // 播完最後一首就從頭開始（你也可以選擇不播）
      }
      playSong(nextIndex);
    });
  </script>

</body>
