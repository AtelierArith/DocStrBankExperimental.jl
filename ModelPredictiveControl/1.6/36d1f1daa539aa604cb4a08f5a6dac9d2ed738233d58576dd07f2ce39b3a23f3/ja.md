```
setstate!(estim::StateEstimator, x̂[, P̂]) -> estim
```

引数 `x̂` から `estim.x̂0` を `x̂ - estim.x̂op` に設定し、適用可能であれば `estim.P̂` を `P̂` に設定します。

共分散誤差推定値 `P̂` は、`estim` がそれを計算する [`StateEstimator`](@ref) の場合にのみ設定できます。
