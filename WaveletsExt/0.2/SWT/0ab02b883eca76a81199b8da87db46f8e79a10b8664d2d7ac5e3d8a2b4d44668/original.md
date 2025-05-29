```
sdwt(x, wt[, L])
```

Computes the stationary discrete wavelet transform (SDWT) for `L` levels.

# Arguments

  * `x::AbstractVector{T}` or `x::AbstractMatrix{T} where T<:Number`: Original signal,   preferably of size 2ᴷ where $K \in \mathbb{N}$.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels of decomposition.

# Returns

`::Matrix{T}` or `::Array{T,3}`: Output from SDWT on `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SDWT
xw = sdwt(x, wt)
```

**See also:** [`swpd`](@ref), [`swpt`](@ref), [`isdwt`](@ref)
