```
histogram_irregular(x::AbstractVector{<:Real}; rule::Str="bayes", grid::String="regular", right::Bool=true, greedy::Bool=true, maxbins::Int=-1, support::Tuple{Real,Real}=(-Inf,Inf), use_min_length::Bool=false, logprior::Function=k->0.0, a::Real=1.0)
```

Create an irregular histogram based on optimization of a criterion based on Bayesian probability, penalized likelihood or LOOCV. Returns a StatsBase.Histogram object with the optimal partition corresponding to the supplied rule.

# Arguments

  * `x`: 1D vector of data for which a histogram is to be constructed.

# Keyword arguments

  * `rule`: The criterion used to determine the optimal number of bins. Defaults to the Bayesian method of Simensen et al. (2025).
  * `grid`: String indicating how the finest possible mesh should be constructed. Options are `"data"`, which uses each unique data point as a grid point, `"regular"` (default) which constructs a fine regular grid, and `"quantile"` which constructs the grid based on the sample quantiles.
  * `right`: Boolean indicating whether the drawn intervals should be right-inclusive or not. Defaults to `true`.
  * `greedy`: Boolean indicating whether or not the greedy binning strategy of Rozenholc et al. (2006) should be used prior to running the dynamical programming algorithm. Defaults to `true`. The algorithm can be quite slow for large datasets when this keyword is set to `false`.
  * `maxbins`: The maximal number of bins to be considered by the optimization criterion, only used if grid is set to "regular" or "quantile". Defaults to `maxbins=min(4*n/log(n)^2, 1000)`. If the specified argument is not a positive integer, the default value is used.
  * `support`: Tuple specifying the the support of the histogram estimate. If the first element is -Inf, then `minimum(x)` is taken as the leftmost cutpoint. Likewise, if the second elemen is `Inf`, then the rightmost cutpoint is `maximum(x)`. Default value is `(-Inf, Inf)`, which estimates the support of the data.
  * `use_min_length`: Boolean indicating whether or not to impose a restriction on the minimum bin length of the histogram. If set to true, the smallest allowed bin length is set to `(maximum(x)-minimum(x))/n*log(n)^(1.5)`.
  * `logprior`: Unnormalized logprior distribution for the number k of bins. Defaults to a uniform prior. Only used in when `rule="bayes"`.
  * `a`: Dirichlet concentration parameter in the Bayesian irregular histogram model. Set to the default value (5.0) if the supplied value is not a positive real number. Only used when `rule="bayes"`.

# Returns

  * `H`: StatsBase.Histogram object with weights corresponding to densities, e.g. `:isdensity` is set to true.

# Examples

```
julia> x = [0.037, 0.208, 0.189, 0.656, 0.45, 0.846, 0.986, 0.751, 0.249, 0.447]
julia> H1 = histogram_irregular(x)
julia> H2 = histogram_irregular(x; grid="quantile", support=(0.0, 1.0), logprior=k->-log(k), a=sqrt(10))
```

...
