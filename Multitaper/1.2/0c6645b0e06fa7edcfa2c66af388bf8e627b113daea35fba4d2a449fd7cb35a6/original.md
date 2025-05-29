```
multispec(S1; <keyword arguments>)
```

Multivariate version of the multispec call, data are in the columns of a matrix ...

# Arguments

  * `S1::Matrix{T} where T<:Float64`: the vector containing the first time series
  * `outp::Symbol`: output can be either :coh for coherence, :justspeccs to compute just the spectra, or :cross for cross-spectra
  * `NW::Float64 = 4.0`: time-bandwidth product of estimate
  * `K::Int64 = 6`: number of slepian tapers, must be <= 2*NW
  * `dt::Float64`: sampling rate in time units
  * `ctr::Bool`: whether or not to remove the mean before computing the multitaper spectrum
  * `pad::Float64 = 1.0`: factor by which to pad the series, i.e. spectrum length will be pad times length of the time series.
  * `dpVec::Union{Matrix{Float64},Nothing} = nothing`: Matrix of dpss's, if they have been precomputed
  * `guts::Bool = false`: whether or not to return the eigencoefficients in the output struct
  * `a_weight::Bool = true`: whether or not to adaptively weight the spectra
  * `jk::Bool = false`: Compute jackknifed confidence intervals
  * `Ftest:Bool = false`: Compute F-test for line components
  * `Tsq::Union{Vector{Int64},Vector{Vector{Int64}},Nothing} = nothing`: which frequency indices to compute the T-squared test for multiple line components. Defaults to none.
  * `alph::Float64 = 0.05`: significance cutoff for the Tsquared test

...

...

# Outputs

  * `Tuple{Vector{MTSpectrum},Vector{P},Union{Float64,Vector{Float64}}} where P = Union{MTCoherence,MTSpectrum}`

struct containing the spectra, coherence or crossspectra, and Tsquared test p-values.  Ouput of middle arg depends on the selection of `outp` input.  ...

See also: [`dpss_tapers`](@ref), [`MTSpectrum`](@ref), [`mdmultispec`](@ref), [`mdslepian`](@ref)
