```julia
linear_combination(basis, θ, x)

```

与えられた順序で、点 `x` における関数基底 $f₁, …$ の線形結合 $∑ θₖ⋅fₖ(x)$ を評価します。

`θ` の長さは `dimension(θ)` に等しい必要があります。
