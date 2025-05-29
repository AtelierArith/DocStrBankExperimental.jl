```
iswpd(xw, wt, L, sm)
iswpd(xw, wt[, L])
iswpd(xw, wt, tree[, sm])
```

Computes the inverse stationary wavelet packet transform (iSWPT) on `xw`.

!!! note
    This function might not be very useful if one is looking to reconstruct a raw decomposed signal. The purpose of this function would be better utilized in applications such as denoising, where a signal is decomposed (`swpd`) and thresholded (`denoise`/`denoiseall`) before being reconstructed.


# Arguments

  * `xw::AbstractArray{T,2}` or `x::AbstractArray{T,3} where T<:Number`: SWPD-transformed array.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)` or `minimum(size(xw)[1:end-1]) |> maxtransformlevels`) Number of levels of decomposition used for reconstruction.
  * `tree::BitVector`: Binary/Quad tree for inverse transform to be computed accordingly.
  * `sm::Integer`: If `sm` is included as an argument, the `sm`-shifted inverse transform will be computed. This results in significantly faster computation, but fails to fully utilize the strength of redundant wavelet transforms.

# Returns

`::Vector{T}` or `::Matrix{T}`: Inverse transformed signal.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SWPD
xw = swpt(x, wt)

# Shift-based iSWPD
x̂ = iswpd(xw, wt, maxtransformlevels(xw,1), 5)

# Average-based iSWPD
x̃ = iswpd(xw, wt)
```

**See also:** [`isdwt_step`](@ref), [`iswpt`](@ref), [`swpd`](@ref), [`iswpd!`](@ref)
