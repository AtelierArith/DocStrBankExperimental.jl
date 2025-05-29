```
histogram_regular(x::AbstractVector{<:Real}; rule::Str="bayes", right::Bool=true, maxbins::Int=1000, support::Tuple{Real,Real}=(-Inf,Inf), logprior::Function=k->0.0, a::Union{Real,Function}=1.0)
```

Create a regular histogram based on optimization criterion from Bayesian probability, penalized likelihood or LOOCV. Returns a StatsBase.Histogram object with regular bins, with the optimal bin number corresponding to the supplied criterion.

...

# Arguments

  * `x`: 1D vector of data for which a histogram is to be constructed.

# Keyword arguments

  * `rule`: The criterion used to determine the optimal number of bins. Defaults to the method Bayesian method of Simensen et al. (2025)
  * `right`: Boolean indicating whether the drawn intervals should be right-inclusive or not. Defaults to `true`.
  * `maxbins`: The maximal number of bins to be considered by the optimization criterion. Ignored if the specified argument is not a positive integer. Defaults to `maxbins=1000`
  * `support`: Tuple specifying the the support of the histogram estimate. If the first element is -Inf, then `minimum(x)` is taken as the leftmost cutpoint. Likewise, if the second element is `Inf`, then the rightmost cutpoint is `maximum(x)`. Default value is `(-Inf, Inf)`, which estimates the support of the data.
  * `logprior`: Unnormalized logprior distribution of the number k of bins. Only used in the case where the supplied rule is `"bayes"`. Defaults to a uniform prior.
  * `a`: Specifies Dirichlet concentration parameter in the Bayesian histogram model. Can either be a fixed positive number or a function computing aₖ for different values of k. Defaults to `1.0` if not supplied. Uses default if suppled value is negative.

# Returns

  * `H`: StatsBase.Histogram object with weights corresponding to densities, e.g. `:isdensity` is set to true.

# Examples

```
julia> x = [0.037, 0.208, 0.189, 0.656, 0.45, 0.846, 0.986, 0.751, 0.249, 0.447]
julia> H1 = histogram_regular(x)
julia> H2 = histogram_regular(x; logprior=k->-log(k), a=k->0.5*k)
```

...
