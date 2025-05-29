```
animate(movie::Movie, scenelist::Vector{Scene};
    creategif = false,
    createmovie = false,
    framerate = 30,
    pathname = "",
    tempdirectory = "")
```

`scenelist`で定義されたシーンの配列を使用して、`movie`のすべてのフレームを作成します。

`creategif`が`true`の場合、アニメーションGIF（".gif"）も作成します。

`createmovie`が`true`の場合、映画（".mkv"、".mp4"、または".webm"）ファイルも作成します。

ファイルは`pathname`キーワード引数に保存されるか、そうでなければ一時ディレクトリに保存されます。

適切な環境では、GIFアニメーションがPlotsウィンドウに表示されます。

### 例

```julia
animate(bang, [
    Scene(bang, backdrop, 0:200),
    Scene(bang, frame1, 0:200, easingfunction=easeinsine)],
    creategif=true,
    pathname="/tmp/animationtest.gif")
```

好みに応じて、生成された静止画像のセットに対してFFMPEG.jlパッケージ（または`ffmpeg`実行可能ファイル）を別途使用することができます。例えば、次のようなコードを使用します：

```julia
using Luxor
using FFMPEG

...

tempdirectory = "/tmp/temp/"

animate(movie, [
        Scene(movie, frame, 1:50)
    ],
    creategif=false,
    tempdirectory=tempdirectory)

FFMPEG.exe(`-r 30 -f image2 -i $(tempdirectory)/%10d.png -c:v libx264 -r 30 -pix_fmt yuv420p -y /tmp/animation.mp4`)

```
