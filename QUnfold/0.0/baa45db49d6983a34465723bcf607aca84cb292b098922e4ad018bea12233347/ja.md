```
predict_with_background(m, X, X_b, α=1) -> Vector{Float64}
```

フィットしたメソッド `m` を用いて、背景測定 `X_b` を `α` でスケーリングした上で、観測データセット `X` におけるクラスの出現率を予測します。
