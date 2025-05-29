```
OneTimescaleAndOscWithMissingModel <: AbstractTimescaleModel
```

Model for inferring a single timescale and oscillation from time series data with missing values. Parameters: [tau, freq, coeff] representing timescale, oscillation frequency, and oscillation coefficient.

# Fields

  * `data::AbstractArray{<:Real}`: Input time series data (may contain NaN)
  * `time::AbstractVector{<:Real}`: Time points corresponding to the data
  * `fit_method::Symbol`: Fitting method (:abc, :advi)
  * `summary_method::Symbol`: Summary statistic type (:psd or :acf)
  * `lags_freqs`: Lags (for ACF) or frequencies (for PSD)
  * `prior`: Prior distribution(s) for parameters
  * `optalg`: Optimization algorithm for :optimization method
  * `distance_method::Symbol`: Distance metric type (:linear or :logarithmic)
  * `data_sum_stats`: Pre-computed summary statistics
  * `dt::Real`: Time step between observations
  * `T::Real`: Total time span
  * `numTrials::Real`: Number of trials/iterations
  * `data_mean::Real`: Mean of input data (excluding NaN)
  * `data_sd::Real`: Standard deviation of input data (excluding NaN)
  * `freqlims`: Frequency limits for PSD analysis
  * `n_lags`: Number of lags for ACF
  * `freq_idx`: Boolean mask for frequency selection
  * `dims::Int`: Dimension along which to compute statistics
  * `distance_combined::Bool`: Whether to use combined distance metric
  * `weights::Vector{Real}`: Weights for combined distance
  * `data_tau::Union{Real, Nothing}`: Pre-computed timescale
  * `data_osc::Union{Real, Nothing}`: Pre-computed oscillation frequency
  * `missing_mask::AbstractArray{Bool}`: Boolean mask indicating NaN positions
