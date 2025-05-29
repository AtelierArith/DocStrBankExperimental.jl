```
cov2cor(C::AbstractMatrix, [s::AbstractArray])
```

共分散行列 `C` から相関行列を計算し、オプションで標準偏差のベクトル `s` を指定します。インプレースバージョンには `StatsBase.cov2cor!` を使用してください。
