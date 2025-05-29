```
acf(x::TS,maxlag::Int=15;lags::AbstractArray{Int,1}=0:maxlag)
acf(x::Vector{T},maxlag::Int=15;lags::AbstractArray{Int,1}=0:maxlag)::Vector{Float64}where{T<:Number}
acf(x::Matrix{T},maxlag::Int=15;lags::AbstractVector{Int}=0:maxlag)::Matrix{Float64}where{T<:Number}
```

Compute the autocorrelation function of a time series.

The output will be a matrix with the same number of columns as the input time series `x` and number of rows equal to the number of lags used as inputs to the autocorrelation function.

...

# Arguments

  * `x::TS`: Time series object array containing columns on which to compute autocorrelation.
  * `maxlag::Int=15`: Maximum lag of the autocorrelation series.

Optional args:

  * `lags::AbstractArray{Int,1}=0:maxlag`: Explicitly specified list of lags to use (overrides use of `maxlag`).

...
