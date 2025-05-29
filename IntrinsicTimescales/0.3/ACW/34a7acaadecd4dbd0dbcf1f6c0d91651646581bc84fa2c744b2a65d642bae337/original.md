```
ACWResults
```

Structure holding ACW analysis inputs and results.

# Fields

  * `data::AbstractArray{<:Real}`: Input time series data
  * `fs::Real`: Sampling frequency
  * `acwtypes::Union{Vector{<:Symbol}, Symbol, Nothing}`: Types of ACW to compute
  * `n_lags::Union{Int, Nothing}`: Number of lags for ACF calculation
  * `freqlims::Union{Tuple{Real, Real}, Nothing}`: Frequency limits for spectral analysis
  * `acw_results::Vector{<:Real}`: Computed ACW values

# Notes

  * Supported ACW types: :acw0, :acw50, :acweuler, :tau, :knee
  * Results order matches input acwtypes order
