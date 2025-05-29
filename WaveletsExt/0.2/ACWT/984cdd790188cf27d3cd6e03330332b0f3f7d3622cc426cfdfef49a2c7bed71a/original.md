```
iacwpdall(xw[, wt, L])
iacwpdall(xw, L)
iacwpdall(xw, wt, tree)
iacwpdall(xw, tree)
```

Computes the inverse autocorrelation wavelet packet decomposition (IACWPD) on each slice of signal.

# Arguments

  * `xw::AbstractArray{T} where T<:Number`: ACWPD-transformed signal.
  * `wt::Union{OrthoFilter, Nothing}`: (Default: `nothing`) Orthogonal wavelet filter.
  * `L::Integer`: (Default: `minimum(size(xw)[1:end-2]) |> maxtransformlevels`) Number of levels of wavelet transforms.
  * `tree::BitVector`: Binary tree for inverse transform to be computed accordingly.

# Returns

  * `::Array{T}`: Slices of reconstructed signals.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate random signals
x = randn(32, 5)
# Create wavelet
wt = wavelet(WT.db4)

# ACWPD on all signals in x
xw = acwpdall(x, wt)

# IACWPD on all signals in xw
x̂ = iacwpdall(xw)
x̂ = iacwpdalll(xw, maketree(x))
x̂ = iacwpdall(xw, 5)
```

**See also:** [`iacwpd`](@ref)
