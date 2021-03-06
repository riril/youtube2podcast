# 下载 youtube 播放列表并生成 podcast

在 `playlists.txt` 文件中填写播放列表的地址（目前只支持一个）。

首先下载播放列表：

```bash
youtube-dl --config-location . --batch-file='./playlists.txt'

# 如果你是私密播放列表的话 可以加上自己的 cookies.txt，这个文件可以通过插件来生成

youtube-dl --config-location . --batch-file='./playlists.txt' --cookies ".\youtube.com_cookies.txt" 
```

生成 `cookies.txt` 的插件：[Get cookies.txt](https://chrome.google.com/webstore/detail/get-cookiestxt/bgaddhkoddajcdgocldbbfleckgcbcid)


安装好依赖，新建一个 `run.py`，你得配置好 operation 的参数，比如：

```py
# run.py
from generate_rss import operation

operation("http://localhost:5000/downloads/")
```

依赖见 `pyproject.toml` > `[tool.poetry.dependencies]`


然后就会生成一个文件 `rss.xml`，然后你就可以把 rss.xml 和生成的 downloads 文件夹移动到公网可见的服务器上。你就可以订阅 podcast 了。

demo 文件：[demo.xml](./demo.xml)


## 参考文档

- [如何使用YouTube-DL从YouTube视频下载MP3轨道](https://www.howtoing.com/download-mp3-track-from-youtube-video-using-youtube-dl)
- [Youtube-dl濃縮教學筆記](https://yogapan.github.io/2017/08/16/Youtube-dl%E6%BF%83%E7%B8%AE%E6%95%99%E5%AD%B8%E7%AD%86%E8%A8%98/)
- [使用youtube-dl下载youtube视频和播放列表](https://blog.webfsd.com/post_shi-yongyoutube-dl-xia-zaiyoutube-shi-pin-he-bo-fang-lie-bia.html)
