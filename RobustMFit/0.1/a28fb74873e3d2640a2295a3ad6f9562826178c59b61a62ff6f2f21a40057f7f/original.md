```
getParams(d::UnivariateDistribution)
```

Selects the parameters of a distribution and gives them out as vector. Only parameters to be estimated are returned.

# Example

```julia
d1 = Normal()
getParams(d1)

d2 = Binomial(10, 0.4)
getParams(d2)
```

See also [`nParEff`](@ref nParEff).
