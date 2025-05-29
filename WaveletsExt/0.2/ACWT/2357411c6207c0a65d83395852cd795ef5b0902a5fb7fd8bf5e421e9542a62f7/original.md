```
acwpt!(xw, x, wt[, L])
```

Same as `acwpt` but without array allocation.

# Arguments

  * `xw::AbstractArray{T} where T<:Number`: Allocation for transformed signal.
  * `x::AbstractArray{T} where T<:Number`: Original signal, preferably of size 2ᴷ or (2ᴷ,2ᴹ) where $K, M \in \mathbb{N}$.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels of decomposition.

# Returns

`xw::Array{T}`: Output from ACWPT on `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPT
xw = Array{Float64,2}(undef, (128,128))
acwpt!(xw, x, wt)
```

**See also:** [`acwpt`](@ref), [`iacwpt`](@ref)
