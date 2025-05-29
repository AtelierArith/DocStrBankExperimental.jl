```
iswpd!(x, xw, wt, L, sm)
iswpd!(x, xw, wt[, L])
iswpd!(x, xw, wt, tree, sm)
iswpd!(x, xw, wt, tree)
```

Same as `iswpd` but with no array allocation.

# Arguments

  * `x::AbstractVector{T}` or `x::AbstractMatrix{T} where T<:Number`: Allocated array for output.
  * `xw::AbstractArray{T,2}` or `xw::AbstractArray{T,3} where T<:Number`: SWPD-transformed array.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)` or `minimum(size(xw)[1:end-1]) |> maxtransformlevels`) Number of levels of decomposition used for reconstruction.
  * `tree::BitVector`: Binary/Quad tree for inverse transform to be computed accordingly.
  * `sm::Integer`: If `sm` is included as an argument, the `sm`-shifted inverse transform will be computed. This results in significantly faster computation, but fails to fully utilize the strength of redundant wavelet transforms.

# Returns

`x::Vector{T}` or `x::Matrix{T}`: Inverse transformed signal.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SWPD
xw = swpd(x, wt)

# ISWPD
x̂ = similar(x)
iswpd!(x̂, xw, wt, 4, 5)
iswpd!(x̂, xw, wt, maketree(x), 5)
iswpd!(x̂, xw, wt, 4)
iswpd!(x̂, xw, wt, maketree(x))
```

**See also:** [`iswpd`](@ref)
