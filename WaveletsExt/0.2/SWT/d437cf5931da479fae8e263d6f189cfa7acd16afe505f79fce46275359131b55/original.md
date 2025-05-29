```
swpt!(xw, x, wt[, L])
```

Same as `swpt` but without array allocation.

# Arguments

  * `xw::AbstractArray{T,2}` or `xw::AbstractArray{T,3} where T<:Number`: Allocation for transformed signal.
  * `x::AbstractVector{T}` or `x::AbstractMatrix{T} where T<:Number`: Original signal, preferably of size 2ᴷ where $K \in \mathbb{N}$.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels of decomposition.

# Returns

`xw::Matrix{T}` or `xw::Array{T,3}`: Output from SWPT on `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SWPT
xw = Array{Float64,2}(undef, (128,128))
swpt!(xw, x, wt)
```

**See also:** [`swpt`](@ref)
