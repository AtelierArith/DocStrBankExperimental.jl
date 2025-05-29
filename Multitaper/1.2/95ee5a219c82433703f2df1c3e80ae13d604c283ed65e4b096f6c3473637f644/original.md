```
mdmultispec(tt, x; <keyword arguments>)
```

Multitaper coherence estimation for multiple time series with the same missing data (gaps)

...

# Arguments

## Keyword Arguments

  * `tt::Vector{T} where T<:Real`: the vector containing the time indices
  * `x::Matrix{P} where P<:Number`: time series in the columns of a matrix

## Positional Arguments

  * `bw = 5/length(tt)`: bandwidth of estimate
  * `k::Int64 = 2*bw*length(x)-1`: number of Slepian tapers, must be `<=

2*bw*length(x)` 

  * `dt = tt[2]-tt[1]`: sampling rate in time units
  * `nz = 0.0`: zero padding factor
  * `Ftest::Bool = false`: Compute the F-test p-value
  * `jk::Bool = true`: Compute jackknifed confidence intervals
  * `lambdau::Union{Tuple{Array{Float64,1},Array{Float64,2}},Nothing} = nothing`:

Slepians, if precomputed

...

...

# Outputs

  * `Tuple{Vector{MTSpectrum},Matrix{MTCoherence},Nothing}` struct containing the spectra,

coherences, and T^2 test significances (currently set to return nothing)

...

See also: [`multispec`](@ref), [`mdslepian`](@ref)
