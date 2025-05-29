```
Simulation(model, frequency; kwargs...)
```

伝播 `model` に基づいて名目上の `frequency` (Hz) のシミュレーションを作成します。`model` は `UnderwaterAcoustics.jl` と互換性のある2½Dまたは3D音響伝播モデルです。

オプションのパラメータ：

  * `irate`: 音響信号のサンプリングのためのADCフレームレート (サンプル/秒)
  * `iblksize`: 音響信号のストリーミングのためのADCブロックサイズ (サンプル、0は自動)
  * `orate`: 音響信号の送信のためのDACフレームレート (サンプル/秒)
  * `txref`: DAC入力と音響ソースレベルとの変換 (dB re µPa @ 1m)
  * `rxref`: 音響受信レベルとADC出力との変換 (dB re 1/µPa)
  * `noise`: シミュレーションのためのノイズモデル (デフォルト: RedGaussianNoise(1e6))

`irate` が指定されていない場合、デフォルトは 4 × `frequency` です。`orate` が指定されていない場合、デフォルトは 8 × `frequency` です。
