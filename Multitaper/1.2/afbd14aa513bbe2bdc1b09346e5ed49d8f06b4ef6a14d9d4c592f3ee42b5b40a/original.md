```
mt_ccvf(S1, S2; <keyword arguments>)
```

Computes bivariate multitaper cross-covariance/cross-correlation function from two time series

...

# Arguments

  * `S1::Vector{T} where T<:Number`: the vector containing the first time series
  * `S2::Vector{T} where T<:Number`: the vector containing the second time series
  * `typ::Symbol`: whether to compute cross-covariance function (:ccvf), or cross-correlation function (:ccf)
  * `NW::Float64 = 4.0`: time-bandwidth product of estimate
  * `K::Int64 = 6`: number of slepian tapers, must be <= 2*NW
  * `dt::Float64`: sampling rate in time units
  * `ctr::Bool`: whether or not to remove the mean before computing the multitaper spectrum
  * `pad::Float64 = 1.0`: factor by which to pad the series, i.e. spectrum length will be pad times length of the time series.
  * `dpVec::Union{Matrix{Float64},Nothing} = nothing`: Matrix of dpss's, if they have been precomputed

...

...

# Outputs

  * `MtCrossCovarianceFunction` struct, depending on the selection of `typ` input above.

...

See also: [`multispec`](@ref)
