```
VideoStream(fig::FigureLike;
        format="mp4", framerate=24, compression=nothing, profile=nothing, pixel_format=nothing, loop=nothing,
        loglevel="quiet", visible=false, connect=false, filter_ticks=true, backend=current_backend(),
        screen_config...)
```

`VideoStream`を返し、新しいフレームをffmpegプロセスに少ないアロケーションでパイプすることができます。完了したら、[`save(path, stream)`](@ref)を使用して、ビデオをファイルに書き出します。

# 引数

## ビデオオプション

  * `format = "mkv"`: ビデオのフォーマット。パスが存在する場合、ファイル拡張子から推測されます。次のいずれかである可能性があります：

      * `"mkv"`  (オープンスタンダード、デフォルト)
      * `"mp4"`  (Webに適している、最もサポートされているフォーマット)
      * `"webm"` (最小のファイルサイズ)
      * `"gif"`  (同じ品質で最大のファイルサイズ)

    `mp4`と`mk4`は`webm`よりもわずかに大きいです。`gif`は品質が悪く（限られたカラーパレットのため）、最大で6倍大きくなる可能性があるため、ビデオがサポートされていないコンテキストで再生する場合を除いて、最後の手段としてのみ使用すべきです。
  * `framerate = 24`: 目標フレームレート。
  * `compression = 20`: `ffmpeg`の`-crf`オプションを介してビデオ圧縮を制御し、数値が小さいほど品質が高く、ファイルサイズが大きく（圧縮が低い）、数値が大きいほど品質が低く、ファイルサイズが小さく（圧縮が高い）なります。最小値は`0`（ロスレスエンコーディング）です。

      * `mp4`の場合、`51`が最大です。`compression = 0`は`profile = "high444"`の場合にのみ`mp4`で機能することに注意してください。
      * `webm`の場合、`63`が最大です。
      * `compression`は`mkv`および`gif`出力には影響しません。
  * `profile = "high422"`: ffmpeg互換のプロファイル。現在は`mp4`にのみ適用されます。ビデオの再生に問題がある場合は、`profile = "high"`または`profile = "main"`を試してください。
  * `pixel_format = "yuv420p"`: ffmpeg互換のピクセルフォーマット（`-pix_fmt`）。現在は`mp4`にのみ適用されます。`profile = "high444"`の場合は`yuv444p`がデフォルトです。
  * `loop = 0`: `gif`または`html`出力のビデオが繰り返される回数。デフォルトは`0`で、無限ループを意味します。`-1`の値はループをオフにし、`n > 0`の値は`n`回の繰り返しを意味します（すなわち、ビデオは`n+1`回再生されます）バックエンドがサポートしている場合。

!!! warning
    `profile`と`pixel_format`は`format`が`"mp4"`のときのみ使用されます。`format`が`"mp4"`でない場合、これら2つの引数が`nothing`でないと警告が発行されます。同様に、`compression`は`format`が`"mp4"`または`"webm"`のときのみ有効です。


## バックエンドオプション

  * `backend=current_backend()`: フレームを記録するために使用されるバックエンド
  * `visible=false`: ウィンドウを表示するかどうか
  * `connect=false`: ウィンドウイベントに接続するかどうか
  * `screen_config...`: バックエンドに渡され、転送できる適用可能なオプションについては、`?Backend.Screen`または`Base.doc(Backend.Screen)`を参照してください。

## その他

  * `filter_ticks`: trueの場合、`tick.state = Makie.OneTimeRenderTick`以外のティックイベントは、`save()`が呼び出されるか、VideoStreamオブジェクトが削除されるまで削除されます。
