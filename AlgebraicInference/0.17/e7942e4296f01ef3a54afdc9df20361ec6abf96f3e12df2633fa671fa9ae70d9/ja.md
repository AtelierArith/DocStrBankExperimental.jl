```
kernel(l::AbstractVector, μ::Real, σ::Real)
```

条件付き分布を次の形で構築します。

$$
p(Y \mid X = x) = \mathcal{N}(l^\mathsf{T}x + \mu, \sigma^2).
$$
