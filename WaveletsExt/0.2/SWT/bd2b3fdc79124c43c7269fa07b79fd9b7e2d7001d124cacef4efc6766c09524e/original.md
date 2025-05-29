```
isdwt(xw, wt[, sm])
```

Computes the inverse stationary discrete wavelet transform (iSDWT) on `xw`.

# Arguments

  * `xw::AbstractArray{T,2}` or `xw::AbstractArray{T,3} where T<:Number`: SDWT-transformed array.
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

# SDWT
xw = sdwt(x, wt)

#  Shift-based iSDWT
x̂ = isdwt(xw, wt, 5)

# Average-based iSDWT
x̃ = isdwt(xw, wt)
```

**See also:** [`isdwt_step`](@ref), [`iswpt`](@ref), [`sdwt`](@ref)
