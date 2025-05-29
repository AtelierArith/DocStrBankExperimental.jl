```
wpd!(y, x, wt[, L])
```

Same as `wpd` but without array allocation.

# Arguments

  * `y::AbstractArray{T,2} where T<:Number` or `y::AbstractArray{T,3} where T<:Number`: An allocated array to write the outputs of `x` onto.
  * `x::AbstractVector{T} where T<:Number` or `x::AbstractArray{T,2} where T<:Number`: Input vector/matrix. A vector input undergoes 1D wavelet decomposition whereas a matrix input undergoes 2D wavelet decomposition.
  * `wt::OrthoFilter`: Wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels for wavelet decomposition.

# Returns

  * `y::AbstractArray{T,2} where T<:Number` or `y::AbstractArray{T,3} where T<:Number`: Decomposed signal. For an input vector, output is a 2D matrix where each column corresponds to a level of decomposition. For an input matrix, output is a 3D array where each slice of dimension 3 corresponds to a level of decomposition.

# Examples:

```
using Wavelets, WaveletsExt

# 1D wavelet decomposition
x = randn(8)
xw = Array{eltype(x)}(undef, (8,3))
wt = wavelet(WT.haar)
wpd!(xw, x, wt)

# 2D wavelet decomposition
x = randn(8,8)
xw = Array{eltype(x)}(undef, (8,8,3))
wt = wavelet(WT.haar)
wpd!(xw, x, wt)
```

**See also:** [`wpd`](@ref), [`iwpd`](@ref)
