```
mvnormcdf(dist::MvNormal, a, b; m::Integer = 1000*size(dist.Σ,1), rng = RandomDevice())
```

Computes the Multivariate Normal probability integral using a quasi-Monte-Carlo algorithm with m points for multivariate normal distributions ([MvNormal](https://juliastats.org/Distributions.jl/stable/multivariate/#Distributions.MvNormal))

Probability p is output with error estimate e.

# Arguments

  * `dist::MvNormal`: multivariate normal distributions from Distributions.jl
  * `a::AbstractVector`: lower integration limit column vector
  * `b::AbstractVector`: upper integration limit column vector
  * `m::Integer`:        number of integration points (default 1000*dimension)
  * `rng`: random number generator

# Reference

  * Genz, A. (1992). Numerical computation of multivariate normal probabilities. Journal of Computational and Graphical Statistics, 1, 141–150
  * Genz, A. (1993). Comparison of methods for the computation of multivariate normal probabilities. Computing Science and Statistics, 25, 400–405
