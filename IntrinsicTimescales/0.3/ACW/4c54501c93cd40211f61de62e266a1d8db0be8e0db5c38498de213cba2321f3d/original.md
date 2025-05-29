```
acw(data, fs; acwtypes=possible_acwtypes, n_lags=nothing, freqlims=nothing, time=nothing, 
    dims=ndims(data), return_acf=true, return_psd=true, average_over_trials=false,
    trial_dims::Int=setdiff([1, 2], dims)[1], max_peaks::Int=1)
```

Compute various autocorrelation width measures for time series data.

# Arguments

  * `data::AbstractArray{<:Real}`: Input time series data
  * `fs::Real`: Sampling frequency
  * `acwtypes::Union{Vector{Symbol}, Symbol}=possible_acwtypes`: Types of ACW to compute
  * `n_lags::Union{Int, Nothing}=nothing`: Number of lags for ACF calculation
  * `freqlims::Union{Tuple{Real, Real}, Nothing}=nothing`: Frequency limits for spectral analysis
  * `time::Union{Vector{Real}, Nothing}=nothing`: Time vector. This is required for Lomb-Scargle method in the case of missing data.
  * `dims::Int=ndims(data)`: Dimension along which to compute ACW (Dimension of time)
  * `return_acf::Bool=true`: Whether to return the ACF
  * `return_psd::Bool=true`: Whether to return the PSD
  * `average_over_trials::Bool=false`: Whether to average the ACF or PSD over trials
  * `trial_dims::Int=setdiff([1, 2], dims)[1]`: Dimension along which to average the ACF or PSD over trials (Dimension of trials)
  * `max_peaks::Int=1`: Maximum number of oscillatory peaks to fit in spectral analysis
  * `oscillation_peak::Bool=true`: Whether to fit an oscillation peak in the spectral analysis

# Returns

  * Vector of computed ACW measures, ordered according to input acwtypes

# Notes

  * Supported ACW types:

      * :acw0 - Time to first zero crossing
      * :acw50 - Time to 50% decay
      * :acweuler - Time to 1/e decay
      * :tau - Exponential decay timescale
      * :knee - Knee frequency from spectral analysis
  * If n_lags is not specified, uses 1.1 * ACW0
  * For spectral measures, freqlims defaults to full frequency range
