```
plotei(model)
plotei!(model)
plotei(model, n, Δ)
plotei!(model, n, Δ)
```

モデルのエイリアスされたスペクトル密度関数を角周波数 `fftfreq(n,2π/Δ)` でプロットします。デフォルトでは、`n = 1024` および `Δ = 1` です。
