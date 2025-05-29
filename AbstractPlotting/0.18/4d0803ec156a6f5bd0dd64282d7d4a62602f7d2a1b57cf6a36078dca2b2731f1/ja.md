```
save(path::String, io::VideoStream[; kwargs...])
```

ビデオストリームをフラッシュし、`path`に見つかった拡張子にファイルを変換します。これは以下のいずれかです：

  * `.mkv`  （デフォルト、変換の必要なし）
  * `.mp4`  （Webに適しており、最もサポートされているフォーマット）
  * `.webm` （最小のファイルサイズ）
  * `.gif`  （同じ品質で最大のファイルサイズ）

`.mp4`と`.mk4`はわずかに大きく、`.gif`は同じ品質で最大6倍大きくなります！

[`VideoStream`](@ref)のドキュメントを参照して、VideoStreamの作成方法を確認してください。よりシンプルなインターフェースを希望する場合は、[`record`](@ref)の使用を検討してください。

### キーワード引数：

  * `framrate = 24`: 目標フレームレート。
  * `compression = 0`: ビデオ圧縮を制御し、`0`がロスレス、`51`が最高圧縮です。`compression = 0`は、`profile = high444`の場合にのみ`.mp4`で機能します。
  * `profile = "high422"`: ffmpeg互換のプロファイル。現在は`.mp4`にのみ適用されます。ビデオ再生に問題がある場合は、`profile = "high"`または`profile = "main"`を試してください。
  * `pixel_format = "yuv420p"`: ffmpeg互換のピクセルフォーマット（pix_fmt）。現在は`.mp4`にのみ適用されます。`profile = high444`の場合は`yuv444p`がデフォルトです。
