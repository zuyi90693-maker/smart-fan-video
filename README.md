# 智能风扇 · 演示视频（网页版）

把 `微信视频2026-10-31_234341_883.mp4`（30.2 MB，竖屏 544×960，H.264，2:53）做成了一个浏览器打开就能播的网页，代码在 git 仓库里，用 GitHub Pages 托管成公网链接。

## 在线地址

- 播放页：<https://zuyi90693-maker.github.io/smart-fan-video/>
- 视频直链：<https://zuyi90693-maker.github.io/smart-fan-video/role-ref.mp4>
- 仓库：<https://github.com/zuyi90693-maker/smart-fan-video>

## 文件说明

| 文件 | 用途 |
| --- | --- |
| `index.html` | 播放页（竖屏适配，含时长/下载/新窗口按钮） |
| `role-ref.mp4` | 视频本体（原文件 `微信视频2026-10-31_234341_883.mp4`） |
| `poster.jpg` | 封面帧（视频第 0 秒） |
| `server.js` | 本地静态服务器，支持 HTTP Range（进度条可拖动） |

## 本地预览（推送前先看效果）

```powershell
cd "D:\deepseek_harnss\talk_work\smart-fan-video"
node server.js 8089
```

打开 <http://127.0.0.1:8089/>，看完 `Ctrl+C` 停掉。

## 以后换视频

1. 用新文件覆盖 `role-ref.mp4`（或改 `index.html` 里的文件名）。
2. 重新截封面：`ffmpeg -ss 3 -i role-ref.mp4 -frames:v 1 -q:v 3 poster.jpg -y`
3. `git add -A; git commit -m "更新视频"; git push`
4. 等 1~2 分钟，刷新播放页链接。

## 注意

- 仓库是**公开**的：任何拿到链接的人都能播放和下载这个视频。不想公开就删仓库或在 Settings 里改私有（私有仓库的 Pages 需要 GitHub Pro，免费账号会失效）。
- 单个文件上限 100 MB；换成更大的视频前先用 `-crf 26` 压一遍。