```
GPoisson(λ::Real, ϕ::Real)
```

The Generalised Poisson distribution with parameters `λ` and `ϕ`, see [Article](https://doi.org/10.1016/j.jmaa.2011.11.042)

# Example

```julia
d = GPoisson(5, 0.7)
mean(d)
pdf(d, 1)
```
