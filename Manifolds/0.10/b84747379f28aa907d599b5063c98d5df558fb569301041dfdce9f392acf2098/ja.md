```
mean(M::Circle{ℝ}, x::AbstractVector[, w::AbstractWeights])
```

Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) を `x` の点の集合である [`Circle`](@ref) $𝕊^1$ 上で計算します。これは実数で表され、すなわち角度の平均を意味します。

$$
\operatorname{atan}\Bigl( \sum_{i=1}^n w_i\sin(x_i),  \sum_{i=1}^n w_i\sin(x_i) \Bigr).
$$
