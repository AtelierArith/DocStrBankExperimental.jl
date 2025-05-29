```
OneTimescaleModel <: AbstractTimescaleModel
```

Model for inferring a single timescale from time series data using the Ornstein-Uhlenbeck process. We recommend using the `one_timescale_model` constructor function rather than creating directly.

# Fields

  * `data::AbstractArray{<:Real}`: Input time series data
  * `time::AbstractVector{<:Real}`: Time points corresponding to the data
  * `fit_method::Symbol`: Fitting method (:abc or :advi)
  * `summary_method::Symbol`: Summary statistic type (:psd or :acf)
  * `lags_freqs`: Lags (for ACF) or frequencies (for PSD)
  * `prior`: Prior distribution(s) for parameters
  * `distance_method::Symbol`: Distance metric type (:linear or :logarithmic)
  * `data_sum_stats`: Pre-computed summary statistics
  * `dt::Real`: Time step between observations
  * `T::Real`: Total time span
  * `numTrials::Real`: Number of trials/iterations
  * `data_mean::Real`: Mean of input data
  * `data_sd::Real`: Standard deviation of input data
  * `freqlims`: Frequency limits for PSD analysis
  * `n_lags`: Number of lags for ACF
  * `freq_idx`: Boolean mask for frequency selection
  * `dims::Int`: Dimension along which to compute statistics
  * `distance_combined::Bool`: Whether to use combined distance metric
  * `weights::Vector{Real}`: Weights for combined distance
  * `data_tau::Union{Real, Nothing}`: Pre-computed timescale
  * `u0::Union{Vector{Real}, Nothing}`: Initial parameter guess
