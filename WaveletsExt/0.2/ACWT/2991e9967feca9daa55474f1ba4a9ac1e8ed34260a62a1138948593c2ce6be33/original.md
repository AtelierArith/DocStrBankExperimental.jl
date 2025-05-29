```
iacwpt!(x, xw[, wt])
```

Same as `iacwpt` but without array allocation.

# Arguments

  * `x::AbstractArray{T} where T<:Number`: Allocated array for output.
  * `xw::AbstractArray{T} where T<:Number`: ACWPD-transformed array.
  * `wt::Union{OrthoFilter, Nothing}`: (Default: `nothing`) Orthogonal wavelet filter.

# Returns

`x::Array{T}`: Inverse transformed signal.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPT
xw = acwpt(x, wt)

# IACWPT
x̂ = similar(x)
iacwpt!(x̂, xw)
```

**See also:** [`iacwpt`](@ref)
