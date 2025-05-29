```
check_differential(M, F, dF, p=rand(M), X=rand(M; vector_at=p); kwargs...)
```

Check numerically whether the differential `dF(M,p,X)` of `F(M,p)` is correct.

This implements the method described in [Boumal:2023; Section 4.8](@cite).

Note that if the errors are below the given tolerance and the method is exact, no plot is generated,

# Keyword arguments

  * `exactness_tol=1e-12`: if all errors are below this tolerance, the differential is considered to be exact
  * `io=nothing`: provide an `IO` to print the result to
  * `limits=(-8.0, 0.0)`: specify the limits in the `log_range`
  * `log_range=range(limits[1], limits[2]; length=N)`: specify the range of points (in log scale) to sample the differential line
  * `N=101`: number of points to verify within the `log_range` default range $[10^{-8},10^{0}]$
  * `name="differential"`: name to display in the plot
  * `plot=false`: whether to plot the result (if `Plots.jl` is loaded). The plot is in log-log-scale. This is returned and can then also be saved.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `slope_tol=0.1`: tolerance for the slope (global) of the approximation
  * `throw_error=false`: throw an error message if the differential is wrong
  * `window=nothing`: specify window sizes within the `log_range` that are used for the slope estimation. The default is, to use all window sizes `2:N`.
