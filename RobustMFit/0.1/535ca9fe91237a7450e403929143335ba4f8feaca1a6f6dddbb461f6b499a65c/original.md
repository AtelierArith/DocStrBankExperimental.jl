```
MTP(μ::Vector{Real}, d::UnivariateDistribution)
```

Mapping moments to parameters of a unviariate distribution. `μ` must be a vector of the first p raw moments of the distribution, given that p is the number of parameters to be estimated. Parameters of the distribution `d` are ignored.

Hardcoded in closed form for 25 commonly used distributions. For some distributions (8) relies on numerical root search if not analytically solvable. Worst case: numerical root search and numerical computation of moments.

# Example

```julia
d1 = Normal()
MTP([1, 5], d1)
d2 = Poisson(10)
MTP([5], d2)
```

See also [`nParEff`](@ref nParEff) for the effective number of parameters and [`PTM`](@ref PTM) for the inverse mapping from parameters to moments. 
