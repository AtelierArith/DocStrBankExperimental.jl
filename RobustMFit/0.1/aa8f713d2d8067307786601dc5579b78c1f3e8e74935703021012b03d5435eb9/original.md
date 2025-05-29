```
CMPDist(λ::Real, ν::Real)
```

The Conway-Maxwell-Poisson distribution with parameters `λ` and `ν`, see [Wikipedia](https://en.wikipedia.org/wiki/Conway%E2%80%93Maxwell%E2%80%93Poisson_distribution)

# Example

```julia
d = CMPDist(5, 0.7)
mean(d)
pdf(d, 1)
```
