```
record(func, figurelike, path; backend=current_backend(), kwargs...)
record(func, figurelike, path, iter; backend=current_backend(), kwargs...)
```

最初のシグネチャは、`func` に VideoStream を提供し、フレームを記録する際に `recordframe!(io)` を呼び出す必要があります。

2 番目のシグネチャは `iter` を反復処理し、現在の反復要素で `func` を呼び出した後に内部で `recordframe!(io)` を呼び出します。

両方の表記法は、動作するために Figure、FigureAxisPlot または Scene `figure` を必要とします。アニメーションは `path` に保存され、フォーマットは `path` の拡張子によって決まります。

内部的には、`record` は単に `video_io = Record(func, figurelike, [iter]; same_kw...); save(path, video_io)` です。`Record` は、後で保存するために直接使用することも、Notebook に直接ビデオをインライン化するために使用することもできます（その目的のために、`show(video_io, "text/html")` がサポートされています）。

# `kwargs...` を介して渡すことができるオプション:

  * `backend::Module = current_backend()`: ビデオを書き出すためのバックエンドを設定します。`CairoMakie`、`GLMakie`、`WGLMakie`、`RPRMakie` に設定できます。

### バックエンドオプション

適用可能なオプションは `?Backend.Screen` または `Base.doc(Backend.Screen)` を参照してください。

### ビデオオプション

  * `format = "mkv"`: ビデオのフォーマット。パスが存在する場合、ファイル拡張子から推測されます。次のいずれかになります:

      * `"mkv"`  (オープンスタンダード、デフォルト)
      * `"mp4"`  (Web に適している、最もサポートされているフォーマット)
      * `"webm"` (最小のファイルサイズ)
      * `"gif"`  (同じ品質で最大のファイルサイズ)

    `mp4` と `mk4` は `webm` よりわずかに大きくなります。`gif` は、品質が悪化する（色パレットが制限されているため）可能性があり、最大で 6 倍大きくなることがあります。ビデオがサポートされていないコンテキストで再生する場合にのみ、最後の手段として使用するべきです。
  * `framerate = 24`: 目標フレームレート。
  * `compression = 20`: `ffmpeg` の `-crf` オプションを介してビデオ圧縮を制御します。小さい数値は高品質で大きなファイルサイズ（低圧縮）を提供し、大きい数値は低品質で小さなファイルサイズ（高圧縮）を提供します。最小値は `0`（ロスレスエンコーディング）です。

      * `mp4` の場合、`51` が最大です。`compression = 0` は `profile = high444` の場合にのみ `mp4` で機能します。
      * `webm` の場合、`63` が最大です。
      * `compression` は `mkv` および `gif` 出力には影響しません。
  * `profile = "high422"`: ffmpeg 互換のプロファイル。現在は `mp4` のみ適用されます。ビデオの再生に問題がある場合は、`profile = "high"` または `profile = "main"` を試してください。
  * `pixel_format = "yuv420p"`: ffmpeg 互換のピクセルフォーマット（`-pix_fmt`）。現在は `mp4` のみ適用されます。`profile = high444` の場合は `yuv444p` がデフォルトです。
  * `loop = 0`: `gif` のビデオが繰り返される回数。デフォルトは `0` で、無限ループを意味します。`-1` の値はループをオフにし、`n > 0` の値は `n` 回の繰り返しを意味します（つまり、ビデオは `n+1` 回再生されます）。

```
!!! warning
`profile` と `pixel_format` は `format` が `"mp4"` の場合にのみ使用されます。`format` が `"mp4"` でない場合、これらの 2 つの引数が `nothing` でないと警告が発行されます。同様に、`compression` は `format` が `"mp4"` または `"webm"` の場合にのみ有効であり、`loop` は `format` が `"gif"` の場合にのみ有効です。
```

# 一般的な使用法

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
        p[:color] = RGBf(i/255, (255 - i)/255, 0) # 図をアニメーション化
        recordframe!(io)
    end
end
```

または

```julia
fig, ax, p = lines(rand(10))
record(fig, "test.gif", 1:255) do i
    p[:color] = RGBf(i/255, (255 - i)/255, 0) # 図をアニメーション化
end
```
