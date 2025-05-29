```
pointwise_prior_logdensities(model, chain[, keytype, context])
```

モデルのチェーンに基づいて、ポイントワイズのログ事前密度を計算します。これは `pointwise_logdensities(model, chain, context)` と同じですが、事前項のみを含みます。詳細は [`pointwise_logdensities`](@ref) を参照してください。
