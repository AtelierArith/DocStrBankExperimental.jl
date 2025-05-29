```
estimate_gpd_parameters(X::AbstractVector{<:Real}, estimator::Symbol)
```

Estimate and return the parameters `σ, ξ` of a Generalized Pareto Distribution fit to `X` (which typically is the exceedances of the log distance of a state space set), assuming that `minimum(X) ≥ 0` and hence the parameter `μ` is 0 (if not, simply shift `X` by its minimum), according to the methods provided in [Pons2023](@cite).

The estimator can be:

  * `:exp`: Assume the distribution is exponential instead of GP and get `σ` from mean of `X` and set `ξ = 0`.
  * `mm`: Standing for "method of moments", estimants are given by

    $$
    \xi = (\bar{x}^2/s^2 - 1)/2, \quad \sigma = \bar{x}(\bar{x}^2/s^2 + 1)/2
    $$

    with $\bar{x}$ the sample mean and $s^2$ the sample variance. This estimator only exists if the true distribution `ξ` value is < 0.5.
