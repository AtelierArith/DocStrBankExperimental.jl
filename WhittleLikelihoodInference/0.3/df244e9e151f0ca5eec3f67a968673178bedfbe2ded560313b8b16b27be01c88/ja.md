```
plotcoh(model)
plotcoh!(model)
plotcoh(model, Ω)
plotcoh!(model, Ω)
```

モデルのコヒーレンスと群遅延を周波数 `Ω` でプロットします。多変量の場合、対角線の上はコヒーレンス、下は群遅延、対角線上はスペクトル密度関数です。デフォルトでは、`Ω = range(-π,π,length=200)` および `Δ = 1` です。
