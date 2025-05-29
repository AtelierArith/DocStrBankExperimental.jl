```
GeneralizedTDist(μ::Real, σ::Real,  ν::Real)
```

The T distribution with parameters `μ`, `σ` and `ν`

# Example

```julia
d = GeneralizedTDist(1, 2, 10)
mean(d)
pdf(d, 1)
```
