```
pointwise_dimensions(X::StateSpaceSet, εs::AbstractVector; kw...) → Δloc
```

各点に対するポイントワイズ次元を返します。すなわち、内部相関和の指数スケーリング

$$
c_q(\epsilon) = \left[\sum_{j:|i-j| > w} B(||X_i - X_j|| < \epsilon)\right]^{q-1}
$$

と $\epsilon$ の関係です。`Δloc[i]` は、`X` の `i` 番目の点に対する $c_q$ の $\epsilon$ に対する指数スケーリング（[`linear_region`](@ref) の呼び出しによって導出される）です。

キーワードは [`correlationsum`](@ref) と同じです。指数スケーリングフィットを行わずに内部相関和を取得するには、同じ入力を使用して `FractalDimensions.pointwise_correlationsums` を使用してください。
