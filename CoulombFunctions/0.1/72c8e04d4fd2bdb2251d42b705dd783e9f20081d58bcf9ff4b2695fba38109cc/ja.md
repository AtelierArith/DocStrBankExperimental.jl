```
coulombs!(F, F′, G, G′, x::AbstractVector, η, ℓ; kwargs...)
```

`x` のすべての値をループ処理し、すべてのクーロン関数を計算し、結果を事前に割り当てられた行列 `F`、`F′`、`G`、`G′` に格納します。
