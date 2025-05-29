```
plotasdf(model)
plotasdf!(model)
plotasdf(model, Ω, Δ)
plotasdf!(model, Ω, Δ)
```

モデルの周波数 Ω におけるエイリアスされたスペクトル密度関数をプロットします。デフォルトでは、`Ω = range(-π,π,length=200)` および `Δ = 1` です。
