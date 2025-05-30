```
SimpleCovariance(;corrected::Bool=false)
```

単純共分散推定器。推定は `cov(x; corrected=corrected)`、`cov(x, y; corrected=corrected)` または `cov(X, w, dims; corrected=corrected)` を呼び出します。ここで、`x`、`y` はベクトル、`X` は行列、`w` は重みベクトルです。
