```
iwpd(x̂, xw, wt[, L])
iwpd(x̂, xw, wt, tree)
```

Same as `iwpd` but without array allocation.

# Arguments

  * `x̂::AbstractVector{T} where T<:Number` or `x̂::AbstractArray{T,2} where T<:Number`: Allocated output vector/matrix for reconstructed signal.
  * `xw::AbstractArray{T,2} where T<:Number` or `xw::AbstractArray{T,3} where T<:Number`: Input array. A 2D input undergoes 1D wavelet reconstruction whereas a 3D input undergoes 2D wavelet reconstruction.
  * `wt::OrthoFilter`: Wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels for wavelet decomposition.
  * `tree::BitVector`: Binary tree or Quadtree to transform to be computed accordingly.

# Returns

  * `x̂::Array{T,1}` or `x̂::Array{T,2}`: Reconstructed signal.

# Examples:

```
using Wavelets, WaveletsExt

# 1D wavelet decomposition
x = randn(8)
wt = wavelet(WT.haar)
xw = wpd(x, wt)
y = similar(x)

# 1D wavelet reconstruction
iwpd!(y, xw, wt)

# 2D wavelet decomposition
x = randn(8,8)
wt = wavelet(WT.haar)
xw = wpd(x, wt)
y = similar(x)

# 2D wavelet reconstruction
iwpd!(y, xw, wt)
```

**See also:** [`iwpd`](@ref), [`iwpt`](@ref)
