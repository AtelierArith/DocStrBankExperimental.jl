```
acwpt(x, wt[, L])
```

Computes `L` levels of autocorrelation wavelet packet transforms (ACWPT) on `x`.

# Arguments

  * `x::AbstractArray{T} where T<:Number`: Original signal, preferably of size 2ᴷ or (2ᴷ,2ᴹ) where $K, M \in \mathbb{N}$.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels of decomposition.

# Returns

`::Array{T}`: Output from ACWPT on `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPT
xw = acwpt(x, wt)
```

**See also:** [`iacwpt`](@ref), [`acdwt`](@ref), [`acwpd`](@ref)
