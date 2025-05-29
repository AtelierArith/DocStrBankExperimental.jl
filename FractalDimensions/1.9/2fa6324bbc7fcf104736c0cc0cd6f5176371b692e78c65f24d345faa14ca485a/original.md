```
slopefit(x, y [, t::SLopeFit]; kw...) → s, s05, s95
```

Fit a linear scaling region in the curve of the two `AbstractVectors` `y` versus `x` using `t` as the estimation method. Return the estimated slope, as well as the confidence intervals for it.

The methods `t` that can be used for the estimation are:

  * [`LinearRegression`](@ref)
  * [`LargestLinearRegion`](@ref) (default)
  * [`AllSlopesDistribution`](@ref)

The keyword `ignore_saturation = true` ignores saturation that (sometimes) happens at the start and end of the curve `y(x)`, where the curve flattens. The keyword `sat_threshold = 0.01` decides what saturation is: while `abs(y[i]-y[i+1]) < sat_threshold` we are in a saturation regime. Said differently, slopes with value `sat_threshold/dx` with `dx = x[i+1] - x[i]` are neglected.

The keyword `ci = 0.95` specifies which quantile (and the 1 - quantile) the confidence interval values are returned at, and by defualt it is 95% (and hence also 5%).
