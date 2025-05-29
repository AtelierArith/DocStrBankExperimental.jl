```
iswpt(xw, wt[, sm])
```

Computes the inverse stationary wavelet packet transform (iSWPT) on `xw`.

# Arguments

  * `xw::AbstractArray{T,2}` or `xw::AbstractArray{T,3} where T<:Number`: SWPT-transformed array.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `sm::Integer`: If `sm` is included as an argument, the `sm`-shifted inverse transform will be computed. This results in significantly faster computation, but fails to fully utilize the strength of redundant wavelet transforms.

# Returns

`::Vector{T}` or `::Matrix{T}`: Inverse transformed signal.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SWPT
xw = swpt(x, wt)

# Shift-based iSWPT
x̂ = iswpt(xw, wt, 5)

# Average-based iSWPT
x̃ = iswpt(xw, wt)
```

**See also:** [`isdwt_step`](@ref), [`isdwt`](@ref), [`swpt`](@ref)
