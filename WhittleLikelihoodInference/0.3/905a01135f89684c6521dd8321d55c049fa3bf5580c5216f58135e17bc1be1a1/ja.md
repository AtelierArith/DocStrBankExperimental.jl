```
plotsdf(model)
plotsdf!(model)
plotsdf(model, Ω)
plotsdf!(model, Ω)
```

モデルのスペクトル密度関数を周波数 `Ω` でプロットします。デフォルトでは、`Ω = range(-π,π,length=200)` および `Δ = 1` です。
