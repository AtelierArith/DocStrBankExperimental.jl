```
record(func, figure, path; framerate = 24, compression = 20, kwargs...)
record(func, figure, path, iter; framerate = 24, compression = 20, kwargs...)
```

最初のシグネチャは、`func` に VideoStream を提供し、フレームを記録する際に `recordframe!(io)` を呼び出す必要があります。

2 番目のシグネチャは `iter` を反復処理し、現在の反復要素で `func` を呼び出した後に内部で `recordframe!(io)` を呼び出します。

両方の表記法は、動作するために Figure、FigureAxisPlot または Scene `figure` を必要とします。

アニメーションは `path` に保存され、フォーマットは `path` の拡張子によって決まります。許可される拡張子は次のとおりです：

  * `.mkv`  (デフォルト、変換の必要なし)
  * `.mp4`  (Web に適しており、最もサポートされているフォーマット)
  * `.webm` (最小のファイルサイズ)
  * `.gif`  (同じ品質で最大のファイルサイズ)

`.mp4` と `.mk4` は `webm` よりもわずかに大きく、`.gif` は同じ品質で最大 6 倍大きくなります！

`compression` 引数は圧縮比を制御します。`51` が最高の圧縮で、`0` または `1` が最低（`0` はロスレス）です。

典型的な使用パターンは次のようになります：

```julia
record(figure, "video.mp4", itr) do i
    func(i) # または図の他の操作
end
```

または、より調整可能な方法として、

```julia
record(figure, "test.gif") do io
    for i = 1:100
        func!(figure)     # 図をアニメーション化
        recordframe!(io)  # 新しいフレームを記録
    end
end
```

より調整可能なインターフェースを希望する場合は、[`VideoStream`](@ref) と [`save`](@ref) の使用を検討してください。

## 拡張ヘルプ

### 例

```julia
fig, ax, p = lines(rand(10))
record(fig, "test.gif") do io
    for i in 1:255
        p[:color] = RGBf0(i/255, (255 - i)/255, 0) # 図をアニメーション化
        recordframe!(io)
    end
end
```

または

```julia
fig, ax, p = lines(rand(10))
record(fig, "test.gif", 1:255) do i
    p[:color] = RGBf0(i/255, (255 - i)/255, 0) # 図をアニメーション化
end
```

### キーワード引数：

  * `framrate = 24`: 目標フレームレート。
  * `compression = 0`: 動画の圧縮を制御し、`0` がロスレスで `51` が最高の圧縮です。`compression = 0` は `.mp4` でのみ `profile = high444` の場合に機能します。
  * `profile = "high422"`: ffmpeg 互換のプロファイル。現在は `.mp4` のみに適用されます。動画の再生に問題がある場合は、`profile = "high"` または `profile = "main"` を試してください。
  * `pixel_format = "yuv420p"`: ffmpeg 互換のピクセルフォーマット (pix_fmt)。現在は `.mp4` のみに適用されます。`profile = high444` の場合は `yuv444p` がデフォルトです。
