```
iswpdall(xw, wt, L, sm)
iswpdall(xw, wt[, L])
iswpdall(xw, wt, tree, sm)
iswpdall(xw, wt, tree)
```

Computes the inverse autocorrelation wavelet packet decomposition (ISWPD) on each slice of signal.

# Arguments

  * `xw::AbstractArray{T} where T<:Number`: SWPD-transformed signal.
  * `wt::Union{OrthoFilter, Nothing}`: (Default: `nothing`) Orthogonal wavelet filter.
  * `L::Integer`: (Default: `minimum(size(xw)[1:end-2]) |> maxtransformlevels`) Number of levels of wavelet transforms.
  * `tree::BitVector`: Binary tree for inverse transform to be computed accordingly.
  * `sm::Integer`: If `sm` is included as an argument, the `sm`-shifted inverse transform will be computed. This results in significantly faster computation, but fails to fully utilize the strength of redundant wavelet transforms.

# Returns

  * `::Array{T}`: Slices of reconstructed signals.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate random signals
x = randn(32, 5)
# Create wavelet
wt = wavelet(WT.db4)

# SWPD on all signals in x
xw = swpdall(x, wt)

# ISWPD on all signals in xw
x̂ = iswpdall(xw)
x̂ = iswpdalll(xw, maketree(x))
x̂ = iswpdall(xw, 5)
```

**See also:** [`iswpd`](@ref)
