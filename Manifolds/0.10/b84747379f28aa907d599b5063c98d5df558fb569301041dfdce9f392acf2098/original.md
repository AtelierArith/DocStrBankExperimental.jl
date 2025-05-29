```
mean(M::Circle{ℝ}, x::AbstractVector[, w::AbstractWeights])
```

Compute the Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) of `x` of points on the [`Circle`](@ref) $𝕊^1$, represented by real numbers, i.e. the angular mean

$$
\operatorname{atan}\Bigl( \sum_{i=1}^n w_i\sin(x_i),  \sum_{i=1}^n w_i\sin(x_i) \Bigr).
$$
