```
acdwt!(xw, x, wt, L)
```

Same as `acdwt` but without array allocation.

# Arguments

  * `xw::AbstractArray{T}`: An allocated array of dimension `(n,L+1)` or `(n,m,3L+1)` to write the outputs of `x` onto.
  * `x::AbstractArray{T} where T<:Number`: Original signal, preferably of size 2ᴷ where $K \in \mathbb{N}$.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels of decomposition.

# Returns

`xw::Array{T,2}`: Output from ACDWT on `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine, 7)
wt = wavelet(WT.haar)

# ACDWT
xw = Matrix{Float64}(undef, (128,5))
acdwt!(xw, x, wt, 4)
```

**See also:** [`acdwt`](@ref)
