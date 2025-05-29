```
BasebandReplayChannel(h, θ, fs, fc, step=1; noise=nothing)
BasebandReplayChannel(h, fs, fc, step=1; noise=nothing)
```

インパルス応答 `h` と位相推定 `θ` を持つベースバンドリプレイチャネルを構築します。位相推定はオプションです。`fs` はサンプリング周波数（Sa/s）、`fc` はキャリア周波数（Hz）、`step` は `h` の時間軸のデシメーションレートです。インパルス応答の有効サンプリング周波数は、1秒あたり `fs ÷ step` のインパルス応答です。

加法性ノイズモデルはオプションで `noise` として指定できます。指定された場合、受信信号を劣化させるために使用されます。
