```
wpd(x, wt[, L])
```

Returns the wavelet packet decomposition (WPD) for L levels for input signal x.

# Arguments

  * `x::AbstractVector{T} where T<:Number` or `x::AbstractArray{T,2} where T<:Number`: Input vector/matrix. A vector input undergoes 1D wavelet decomposition whereas a matrix input undergoes 2D wavelet decomposition.
  * `wt::OrthoFilter`: Wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels for wavelet decomposition.

# Returns

  * `::Array{T,2}` or `::Array{T,3}`: Decomposed signal. For an input vector `x`, output is a 2D matrix where each column corresponds to a level of decomposition. For an input matrix `x`, output is a 3D array where each slice of dimension 3 corresponds to a level of decomposition.

# Examples:

```julia
using Wavelets, WaveletsExt

# 1D wavelet decomposition
x = randn(8)
wt = wavelet(WT.haar)
xw = wpd(x, wt)

# 2D wavelet decomposition
x = randn(8,8)
wt = wavelet(WT.haar)
xw = wpd(x, wt)
```

**See also:** [`wpd!`](@ref), [`iwpd`](@ref)
