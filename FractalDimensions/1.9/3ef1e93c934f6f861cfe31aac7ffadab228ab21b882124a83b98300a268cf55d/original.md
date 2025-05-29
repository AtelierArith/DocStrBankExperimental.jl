```
estimate_gev_scale(X::AbstractVector{<:Real})
```

Estimate and return the scale parameter σ of a Generalized Extreme Value distribution fit to `X`, assuming that the parameter `ξ` is 0. The estimator through the method of moments is given by     σ = √((̄x²-̄x^2)/(π^2/6)) This function is given to improve performance, since for the computation of the local dimension and the location parameter are not necesary to estimate the dimension.
