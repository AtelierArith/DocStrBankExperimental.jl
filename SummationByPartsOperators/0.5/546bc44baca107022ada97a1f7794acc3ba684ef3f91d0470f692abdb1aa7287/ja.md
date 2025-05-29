```
mul!(du, D::DerivativeOperator, u, α=true, β=false)
```

`du = α * D * u + β * du` の効率的なインプレースバージョンです。`du` は `u` とエイリアスされてはいけません。
