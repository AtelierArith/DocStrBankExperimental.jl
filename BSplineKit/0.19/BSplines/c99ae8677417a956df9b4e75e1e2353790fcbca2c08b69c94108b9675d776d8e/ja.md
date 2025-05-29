```
evaluate(B::AbstractBSplineBasis, i::Integer, x,
         [op::AbstractDifferentialOp], [T=Float64])
```

与えられた基底における $i$ 番目の基底関数を `x` で評価します（座標または座標のベクトルである可能性があります）。

導関数を評価するには、`op` 引数として `Derivative(n)` を渡します。ここで、`n` は導関数の次数です。

`Derivative(n) + λ Derivative(m)` のようなより一般的な微分演算子もサポートされています。

[`evaluate!`](@ref) も参照してください。
