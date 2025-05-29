```
kernel(L::AbstractMatrix, μ::AbstractVector, Σ::AbstractMatrix)
```

Construct a conditional distribution of the form

$$
p(Y \mid X = x) = \mathcal{N}(Lx + \mu, \Sigma).
$$
