```
iacwpt(xw[, wt])
```

Computes the inverse autocorrelation wavelet packet transform (IACWPT) on `xw`.

!!! note
    The inverse autocorrelation transform does not require any wavelet filter, but an optional `wt` positional argument is included for the standardization of syntax with `wpt` and `swpt`, but is ignored during the reconstruction of signals.


# Arguments

  * `xw::AbstractArray{T} where T<:Number`: ACWPT-transformed array.
  * `wt::Union{OrthoFilter, Nothing}`: (Default: `nothing`) Orthogonal wavelet filter.

# Returns

`::Array{T}`: Inverse transformed signal.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPT
xw = acwpt(x, wt)

# IACWPT
x̃ = iacwpt(xw)
```

**See also:** [`iacdwt`](@ref), [`acwpt`](@ref)
