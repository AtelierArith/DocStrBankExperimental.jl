```
log_audios(logger::TBLogger, name::AbstractString, samples::AbstractArray, samplerate::Real; step=step(logger))
```

ステップ `step` で複数のオーディオクリップをログします

  * samples:   サンプルの配列 N*C のオーディオクリップの配列で、N はサンプルの数、C はチャンネルの数
  * samplerate: サンプリングレートまたはサンプリング周波数: すべてのクリップに対して同じ実数値
