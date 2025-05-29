```
PTM(d::UnivariateDistribution)
```

Mapping parameters to moments of a unviariate distribution. Returns the first p raw moments of the distribution, given that p is the number of parameters to be estimated. Relies on numerical integration of no closed form for moments is implemented.

# Example

```julia
d1 = Normal()
PTM(d1)
d2 = Binomial(10, 0.4)
PTM(d2)
```

See also [`nParEff`](@ref nParEff) for the effective number of parameters and [`MTP`](@ref MTP) for the inverse mapping from moments to parameters. 
