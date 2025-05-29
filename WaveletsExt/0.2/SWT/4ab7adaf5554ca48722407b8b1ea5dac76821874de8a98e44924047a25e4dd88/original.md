```
sdwt!(xw, x, wt[, L])
```

Same as `sdwt` but without array allocation.

# Arguments

  * `xw::AbstractArray{T,2}` or `xw::AbstractArray{T,3} where T<:Number`: An allocated array of dimension `(n,L+1)` to write the outputs of `x` onto.
  * `x::AbstractVector{T}` or `x::AbstractMatrix{T} where T<:Number`: Original signal, preferably of size 2ᴷ where $K \in \mathbb{N}$.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels of decomposition.

# Returns

`xw::Array{T,2}` or `xw::Array{T,3}`: Output from SDWT on `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine, 7)
wt = wavelet(WT.haar)

# SDWT
xw = Matrix{Float64}(undef, (128,5))
sdwt!(xw, x, wt, 4)
```

**See also:** [`sdwt`](@ref)
