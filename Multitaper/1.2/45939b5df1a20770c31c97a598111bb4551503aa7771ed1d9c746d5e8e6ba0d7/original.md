```
mt_acvf(S1; <keyword arguments>)
```

Computes univariate multitaper autocovariance function starting with an input time series. ...

# Arguments

  * `S1::Vector{T} where T<:Number`: the vector containing the time series
  * `NW::Float64 = 4.0`: time-bandwidth product of estimate
  * `K::Int64 = 6`: number of slepian tapers, must be <= 2*NW
  * `dt::Float64`: sampling rate in time units
  * `ctr::Bool`: whether or not to remove the mean before computing the multitaper spectrum
  * `pad::Float64 = 1.0`: factor by which to pad the series, i.e. spectrum length will be pad times length of the time series.
  * `dpVec::Union{Matrix{Float64},Nothing} = nothing`: Matrix of dpss's, if they have been precomputed
  * `egval::Union{Vector{Float64},Nothing} = nothing`: Vector of concentratins of said dpss's
  * `a_weight::Bool = true`: whether or not to use adaptive weighting

...

...

# Outputs

  * `MTAutocovarianceFunction` struct containing the autocovariance function

...

See also: [`multispec`](@ref)
