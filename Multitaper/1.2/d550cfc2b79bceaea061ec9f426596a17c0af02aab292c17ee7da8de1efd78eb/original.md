```
multispec(S1, S2; <keyword arguments>)
```

Computes multitaper cross-spectrum or coherence when given two time series with same sampling.

...

# Arguments

  * `S1::Union{Vector{T},EigenCoefficient} where T<:Number`: the vector containing the first time

series

  * `S2::Union{Vector{P},EigenCoefficient} where P<:Number`: the vector containing the second

time series

  * `outp::Symbol`: output can be either :coh for coherence, :spec for cross-spectrum,

or :transf for transfer function

  * `NW::Float64 = 4.0`: time-bandwidth product of estimate
  * `K::Int64 = 6`: number of slepian tapers, must be <= 2*NW
  * `offset::Union{Float64,Int64} = 0` set to nonzero value if offset coherence or

cross-spectrum is desired. If Float64 is used, this will be converted to nearest FFT bin.

  * `dt::Float64`: sampling rate in time units
  * `ctr::Bool`: whether or not to remove the mean before computing the multitaper

spectrum

  * `pad::Float64 = 1.0`: factor by which to pad the series, i.e. spectrum length will

be pad times length of the time series.

  * `dpVec::Union{Matrix{Float64},Nothing} = nothing`: Matrix of dpss's, if they have

been precomputed

  * `guts::Bool = false`: whether or not to return the eigencoefficients in the output

struct

  * `jk::Bool = true`: Compute jackknifed confidence intervals
  * `Tsq::Union{Vector{Int64},Vector{Vector{Int64}},Nothing} = nothing`: which

frequency indices to compute the T-squared test for multiple line components. Defaults to none.

  * `alph::Float64 = 0.05`: significance cutoff for the Tsquared test

...

...

# Outputs

  * `MTSpectrum`, `MTCoherence`, or `MTTransferFunction` struct containing the spectrum, coherence or

transfer function, depending on the selection of `outp` input. 

...

See also: [`dpss_tapers`](@ref), [`MTSpectrum`](@ref), [`mdmultispec`](@ref), [`mdslepian`](@ref)
