```
acwpd!(xw, x, wt[, L])
```

Same as `acwpd` but without array allocation.

# Arguments

  * `xw::AbstractArray{T} where T<:Number`: Allocated array for output.
  * `x::AbstractArray{T} where T<:Number`: Original signal, preferably of size 2ᴷ where $K \in \mathbb{N}$.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels of decomposition.

# Returns

`xw::Array{T}`: Output from ACWPD on `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPD
xw = Matrix{Float64}(undef, (128, 255))
acwpd!(xw, x, wt)
acwpd!(xw, x, wt, 7)
```

**See also:** [`acwpd!`](@ref)
