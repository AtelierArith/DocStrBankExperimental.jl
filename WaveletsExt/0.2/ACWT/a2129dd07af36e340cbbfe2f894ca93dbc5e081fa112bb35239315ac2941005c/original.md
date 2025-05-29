```
acdwt(x, wt[, L])
```

Performs a discrete autocorrelation wavelet transform for a given signal `x`. The signal can be 1D or 2D. The wavelet type `wt` determines the transform type. Refer to Wavelet.jl for a list of available methods.

# Arguments

  * `x::AbstractArray{T} where T<:Number`: Original signal, preferably of size 2ᴷ where $K   \in \mathbb{N}$.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels of decomposition.

# Returns

`::Array{T}`: Output from ACDWT on `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACDWT
acdwt(x, wt)
acdwt(x, wt, 4) # level 4 decomposition
```

**See also:** [`acdwt_step`](@ref), [`iacdwt`](@ref), [`acdwt!`](@ref)
