```
multispec(S1; <keyword arguments>)
```

Computes univariate multitaper spectra with a handful of extra gadgets. 

...

# Arguments

  * `S1::Vector{T} where T<:Float64`: the vector containing the time series
  * `NW::Float64 = 4.0`: time-bandwidth product of estimate
  * `K::Int64 = 6`: number of slepian tapers, must be <= 2*NW
  * `dt::Float64`: sampling rate in time units
  * `ctr::Bool`: whether or not to remove the mean before computing the multitaper spectrum
  * `pad::Float64 = 1.0`: factor by which to pad the series, i.e. spectrum length will be pad times length of the time series.
  * `dpVec::Union{Matrix{Float64},Nothing} = nothing`: Matrix of dpss's, if they have been precomputed
  * `egval::Union{Vector{Float64},Nothing} = nothing`: Vector of concentratins of said dpss's
  * `guts::Bool = false`: whether or not to return the eigencoefficients in the output struct
  * `a_weight::Bool = true`: whether or not to use adaptive weighting
  * `Ftest::Bool = true`: Compute the F-test p-value
  * `highres::Bool = false`: Whether to return a "high resolution" spectrum estimate
  * `jk::Bool = true`: Compute jackknifed confidence intervals
  * `Tsq::Union{Vector{Int64},Vector{Vector{Int64}},Nothing} = nothing`: which frequency indices to compute the T-squared test for multiple line components. Defaults to none.

...

...

# Outputs

  * `MTSpectrum` struct containing the spectrum

...

See also: [`dpss_tapers`](@ref), [`MTSpectrum`](@ref), [`mdmultispec`](@ref), [`mdslepian`](@ref)
