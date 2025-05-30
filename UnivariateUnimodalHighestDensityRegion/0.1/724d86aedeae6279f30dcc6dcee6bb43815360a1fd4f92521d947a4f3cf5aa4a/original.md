```
univariate_unimodal_HDR(d::UnivariateDistribution, region::Real, num_steps::Int)
```

A grid-based approach to find the highest density region (HDR) of a univariate, unimodal distribution. Returns the found HDR interval as a vector with length two.

# Arguments

  * `d`: a `UnivariateDistribution` defined in [Distributions.jl](https://juliastats.org/Distributions.jl/stable/).
  * `region`: a real number ∈ [0, 1] specifying the proportion of the density of `d` of the highest density region.
  * `num_steps`: the number of steps to linearly space between the left and right of the bracket, inclusive, where `l=0.0` and `r=1.0-region`. The lower and upper quantiles, `region` apart, at each of these steps is then calculated. The the lower and upper quantile at these steps with the minimum distance between them is estimated to be the HDR. `num_steps` is enforced to be at least 3 and odd to allow exact accuracy on symmetric distributions.
