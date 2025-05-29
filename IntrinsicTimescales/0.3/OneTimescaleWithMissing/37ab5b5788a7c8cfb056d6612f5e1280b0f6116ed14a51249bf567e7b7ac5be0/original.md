```
one_timescale_with_missing_model(data, time, fit_method; kwargs...)
```

Construct a OneTimescaleWithMissingModel for time series analysis with missing data.

# Arguments

  * `data`: Input time series data (may contain NaN)
  * `time`: Time points corresponding to the data
  * `fit_method`: Fitting method to use (:abc or :advi)

# Keyword Arguments

  * `summary_method=:acf`: Summary statistic type (:psd or :acf)
  * `data_sum_stats=nothing`: Pre-computed summary statistics
  * `lags_freqs=nothing`: Custom lags or frequencies
  * `prior=nothing`: Prior distribution(s) for parameters
  * `n_lags=nothing`: Number of lags for ACF
  * `distance_method=nothing`: Distance metric type
  * `dt=time[2]-time[1]`: Time step
  * `T=time[end]`: Total time span
  * `numTrials=size(data,1)`: Number of trials
  * `data_mean=nanmean(data)`: Data mean (excluding NaN)
  * `data_sd=nanstd(data)`: Data standard deviation (excluding NaN)
  * `freqlims=nothing`: Frequency limits for PSD
  * `freq_idx=nothing`: Frequency selection mask
  * `dims=ndims(data)`: Analysis dimension
  * `distance_combined=false`: Use combined distance
  * `weights=[0.5, 0.5]`: Distance weights
  * `data_tau=nothing`: Pre-computed timescale

# Returns

  * `OneTimescaleWithMissingModel`: Model instance configured for specified analysis method

# Notes

Four main usage patterns:

1. ACF-based ABC/ADVI: `summary_method=:acf`, `fit_method=:abc/:advi`
2. PSD-based ABC/ADVI: `summary_method=:psd`, `fit_method=:abc/:advi`
