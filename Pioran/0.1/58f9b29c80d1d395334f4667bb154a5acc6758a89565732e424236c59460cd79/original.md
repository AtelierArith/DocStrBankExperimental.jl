```
extract_subset(rng, prefix, t, y, yerr; n_perc=0.03, take_log=true, suffix="")
extract_subset(seed, prefix, t, y, yerr; n_perc=0.03, take_log=true)
```

Extract a subset of the data for the analysis and return initial guesses for the mean and variance. Either a random number generator or a seed can be provided.

# Arguments

  * `seed::Int64` : Seed for the random number generator.
  * `rng::AbstractRNG` : Random number generator.
  * `prefix::String` : Prefix for the output files.
  * `t::Array{Float64,1}` : Time array.
  * `y::Array{Float64,1}` : Time series array.
  * `yerr::Array{Float64,1}` : Time series error array.
  * `n_perc::Float64` : Percentage of the time series to extract.
  * `take_log::Bool` : If true, log transform the time series for the estimation of the mean and variance.
  * `suffix::String` : Suffix for the output files.

# Return

  * `t_subset::Array{Float64,1}` : Time array of the subset.
  * `y_subset::Array{Float64,1}` : Time series array of the subset.
  * `yerr_subset::Array{Float64,1}` : Time series error array of the subset.
  * `x̄::Float64` : Mean of the normal distribution for μ.
  * `va::Float64` : Variance of the normal distribution for μ.
