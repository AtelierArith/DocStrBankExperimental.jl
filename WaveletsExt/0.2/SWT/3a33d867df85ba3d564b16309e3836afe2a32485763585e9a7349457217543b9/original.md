```
isdwt!(x, xw, wt[, sm])
```

Same as `isdwt` but with no array allocation.

# Arguments

  * `x::AbstractVector{T}` or `x::AbstractMatrix{T} where T<:Number`: Allocation for reconstructed signal.
  * `xw::AbstractArray{T,2}` or `xw::AbstractArray{T,3} where T<:Number`: SDWT-transformed array.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `sm::Integer`: If `sm` is included as an argument, the `sm`-shifted inverse transform will be computed. This results in significantly faster computation, but fails to fully utilize the strength of redundant wavelet transforms.

# Returns

`x::Vector{T}` or `x::Matrix{T}`: Inverse transformed signal.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SDWT
xw = sdwt(x, wt)

#  Shift-based iSDWT
x̂ = similar(x)
isdwt!(x̂, xw, wt, 5)

# Average-based iSDWT
isdwt(x̂, xw, wt)
```

**See also:** [`isdwt`](@ref)
