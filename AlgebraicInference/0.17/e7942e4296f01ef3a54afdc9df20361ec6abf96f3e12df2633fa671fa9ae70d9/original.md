```
kernel(l::AbstractVector, μ::Real, σ::Real)
```

Construct a conditional distribution of the form

$$
p(Y \mid X = x) = \mathcal{N}(l^\mathsf{T}x + \mu, \sigma^2).
$$
