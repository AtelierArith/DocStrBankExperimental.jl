```
iacdwt(xw[, wt])
```

Performs the inverse autocorrelation discrete wavelet transform. Can be used for both the 1D and 2D case.

!!! note
    The inverse autocorrelation transform does not require any wavelet filter, but an optional `wt` positional argument is included for the standardization of syntax with `dwt` and `sdwt`, but is ignored during the reconstruction of signals.


# Arguments

  * `xw::AbstractArray{T} where T<:Number`: ACDWT-transformed array.
  * `wt::Union{OrthoFilter, Nothing}`: (Default: `nothing`) Orthogonal wavelet filter.

# Returns

`::Array{T}`: Inverse transformed signal.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACDWT
xw = acdwt(x, wt)

# IACDWT
x̃ = iacdwt(xw)
```

**See also:** [`acdwt`](@ref), [`iacdwt_step!`](@ref)
