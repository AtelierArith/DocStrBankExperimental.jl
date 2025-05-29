```
log_audio(logger::TBLogger, name::AbstractString, samples::AbstractArray, samplerate::Real; step=step(logger))
```

名前 `name` のオーディオクリップをステップ `step` でログします。

  * samples: サンプルの配列 N*C で、N = サンプル数、C = チャンネル数
  * samplerate: サンプリングレートまたはサンプリング周波数: 実数値
