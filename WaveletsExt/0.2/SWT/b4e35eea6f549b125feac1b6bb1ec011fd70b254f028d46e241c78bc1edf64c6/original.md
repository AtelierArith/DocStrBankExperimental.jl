```
swpd!(xw, x, wt[, L])
```

Same as `swpd` but without array allocation.

# Arguments

  * `xw::AbstractArray{T,2}` or `xw::AbstractArray{T,3} where T<:Number`: Allocation for transformed signal.
  * `x::AbstractVector{T}` or `x::AbstractMatrix{T} where T<:Number`: Original signal, preferably of size 2ᴷ where $K \in \mathbb{N}$.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels of decomposition.

# Returns

`xw::Matrix{T}` or `xw::Array{T,3}`: Output from SWPD on `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SWPD
xw = Matrix{T}(undef, (128, 255))
swpd!(xw, x, wt)
```

**See also:** [`swpd`](@ref)
