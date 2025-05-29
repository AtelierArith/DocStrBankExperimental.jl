```
BaseModel <: AbstractTimescaleModel
```

Base model structure for timescale inference using various methods.

# Fields

  * `data`: Input time series data
  * `time`: Time points corresponding to the data
  * `data_sum_stats`: Pre-computed summary statistics of the data
  * `fitmethod::Symbol`: Fitting method to use. Options: `:abc`, `:advi`, `:acw`
  * `summary_method::Symbol`: Summary statistic type. Options: `:psd` (power spectral density) or `:acf` (autocorrelation)
  * `lags_freqs::AbstractVector{<:Real}`: Lags (for ACF) or frequencies (for PSD) at which to compute summary statistics
  * `prior`: Prior distributions for parameters. Can be Vector{Distribution}, single Distribution, or "informed_prior"
  * `acwtypes::Union{Vector{Symbol}, Symbol}`: ACW analysis types (e.g., :ACW50, :ACW0, :ACWe, :tau, :knee)
  * `distance_method::Symbol`: Distance metric type. Options: `:linear` or `:logarithmic`
  * `dt::Real`: Time step between observations
  * `T::Real`: Total time span of the data
  * `numTrials::Real`: Number of trials/iterations
  * `data_mean::Real`: Mean of the input data
  * `data_sd::Real`: Standard deviation of the input data
