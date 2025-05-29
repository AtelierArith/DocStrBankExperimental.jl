```
mean(M::Circle{ℝ}, x::AbstractVector[, w::AbstractWeights])
```

Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) を `x` の点の集合で計算します [`Circle`](@ref) $𝕊^1$ 上の、実数で表される、すなわち角度の平均

$$
\operatorname{atan}\Bigl( \sum_{i=1}^n w_i\sin(x_i),  \sum_{i=1}^n w_i\cos(x_i) \Bigr).
$$
