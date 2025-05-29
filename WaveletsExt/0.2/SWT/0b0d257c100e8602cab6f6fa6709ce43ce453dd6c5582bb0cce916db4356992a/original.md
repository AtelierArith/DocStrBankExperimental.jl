```
swpd(x, wt[, L])
```

Computes `L` levels of stationary wavelet packet decomposition (SWPD) on `x`.

# Arguments

  * `x::AbstractVector{T}` or `x::AbstractMatrix{T} where T<:Number`: Original signal, preferably of size 2ᴷ where $K \in \mathbb{N}$.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels of decomposition.

# Returns

`::Matrix{T}` or `::Array{T,3}`: Output from SWPD on `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SWPD
xw = swpd(x, wt)
```

**See also:** [`iswpd`](@ref), [`swpt`](@ref)
