```
sinusoidal(;duration::Real, amplitude::Real=one(start))
```

次の式の正弦波形を作成します。

```julia
amplitude * sin(2π*t)
```

# キーワード引数

  * `duration`: 波形の持続時間。
  * `amplitude`: 正弦波の振幅。
