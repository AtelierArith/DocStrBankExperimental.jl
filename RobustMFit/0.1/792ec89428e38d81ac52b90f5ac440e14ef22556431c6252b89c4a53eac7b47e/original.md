```
MTPder(μ::Vector{Real}, d::UnivariateDistribution)
```

Derivative of the mapping from moments to parameters of a unviariate distribution. `μ` must be a vector of the first p raw moments of the distribution, given that p is the number of parameters to be estimated. Parameters of the distribution `d` are ignored.

Hardcoded in closed form for 25 commonly used distributions. For other distributions relies on the numerical gradient.

Output is a matrix where i-th row and j-th column gives the derivative of j-th parameter w.r.t the i-th moment.

# Example

```julia
d1 = Normal()
MTP([1, 5], d1)
d2 = Poisson(10)
MTP([5], d2)
```

See also [`nParEff`](@ref nParEff) for the effective number of parameters and [`MTP`](@ref MTP) for the mapping from moments to parameters. 
