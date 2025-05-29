```
pointwise_loglikelihoods(model, chain[, keytype, context])
```

モデルの与えられたチェーンに対するポイントワイズ対数尤度を計算します。これは `pointwise_logdensities(model, chain, context)` と同じですが、尤度項のみを含みます。参照: [`pointwise_logdensities`](@ref)。
