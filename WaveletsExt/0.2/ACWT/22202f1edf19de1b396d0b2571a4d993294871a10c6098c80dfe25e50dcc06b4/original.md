```
iacwpd(xw, L)
iacwpd(xw[, wt, L])
iacwpd(xw, tree)
iacwpd(xw, wt, tree)
```

Performs the inverse autocorrelation discrete wavelet packet transform, with respect to a decomposition tree.

!!! note
    The inverse autocorrelation transform does not require any wavelet filter, but an optional `wt` positional argument is included for the standardization of syntax with `wpt` and `swpt`, but is ignored during the reconstruction of signals.


!!! note
    This function might not be very useful if one is looking to reconstruct a raw decomposed signal. The purpose of this function would be better utilized in applications such as denoising, where a signal is decomposed (`swpd`) and thresholded (`denoise`/`denoiseall`) before being reconstructed.


# Arguments

  * `xw::AbstractArray{T} where T<:Number`: ACWPD-transformed array.
  * `wt::Union{OrthoFilter, Nothing}`: (Default: `nothing`) Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels of decomposition used for reconstruction.
  * `tree::BitVector`: Binary tree for inverse transform to be computed accordingly.

# Returns

`::Array{T}`: Inverse transformed signal.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPD
xw = acwpd(x, wt)

# IACWPD
x̂ = iacwpd(xw, 4)
x̂ = iacwpd(xw, wt, 4)
x̂ = iacwpd(xw, maketree(x))
x̂ = iacwpd(xw, wt, maketree(x))
```

**See also:** [`acwpd`](@ref)
