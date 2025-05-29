```
GSDist(dist::UnivariateDistribution, F₀::Real=0.5;
n::Int=21, diff::Function=three_point_midpoint, h::Real=1.0)
```

# Arguments

  * `dist::UnivariateDistribution`: a univariate distribution.
  * `F₀::Real`: the reference quantile to center the distribution around.
  * `n::Integer`: the number of points on the distribution to use for least squares fit.
  * `diff::Function`: one of the finite difference methods for gradient approximation.
  * `h::Real`: the denominator used in the diff function.
