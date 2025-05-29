```
mdmultispec(tt, x; <keyword arguments>)
```

Multitaper power spectrum estimation for time series with missing data (gaps)

...

# Arguments

## Positional Arguments

  * `tt::Vector{T} where T<:Real`: the vector containing the time indices
  * `x::Vector{P} where P<:Number`: data vector

## Keyword Arguments

  * `bw = 5/length(tt)`: bandwidth of estimate
  * `k::Int64 = 2*bw*length(x)-1`: number of Slepian tapers, must be `<=

2*bw*length(x)` 

  * `dt::T = tt[2]-tt[1]`: sampling rate in time units
  * `nz = 0.0`: zero padding factor
  * `Ftest::Bool = true`: Compute the F-test p-value
  * `jk::Bool = true`: Compute jackknifed confidence intervals
  * `dof::Bool = false`: Compute degrees of freedom for the adaptively weighted

spectrum estimate

  * `lambdau::Union{Tuple{Array{Float64,1},Array{Float64,2}},Nothing} = nothing`:

Slepians, if precomputed ...

...

# Outputs

  * `pkg::MTSpectrum` struct containing the spectrum
  * `nu1::Vector{Float64}` optional vector containing the degrees of freedom, given

if the `dof` kwarg is set to `true`.

...

See also: [`multispec`](@ref), [`mdslepian`](@ref)
