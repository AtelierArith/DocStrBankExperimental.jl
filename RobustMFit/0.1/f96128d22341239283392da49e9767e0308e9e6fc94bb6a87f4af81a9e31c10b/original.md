```
FInfo(d::UnivariateDistribution)
```

Fisher Information matrix for distribution `d`.

Hardcoded for commonly used distributions. If no closed form known, the function is based on numerical computation of gradients and expectations.

# Example

```julia
d = Poisson(10)
FInfo(d)

d = Normal(0, 1)
FInfo(d)
```

See also [`RAE`](@ref RAE).
