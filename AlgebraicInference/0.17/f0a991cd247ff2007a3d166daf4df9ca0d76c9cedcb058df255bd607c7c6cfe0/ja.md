```
kernel(L::AbstractMatrix, μ::AbstractVector, Σ::AbstractMatrix)
```

条件付き分布を次の形で構築します。

$$
p(Y \mid X = x) = \mathcal{N}(Lx + \mu, \Sigma).
$$
