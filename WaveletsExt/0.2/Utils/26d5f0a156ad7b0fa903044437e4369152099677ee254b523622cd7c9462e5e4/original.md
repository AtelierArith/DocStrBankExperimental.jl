```
coarsestscalingrange(x, tree[, redundant])
coarsestscalingrange(n, tree[, redundant])
```

Given a binary tree, returns the index range of the coarsest scaling coefficients.

# Arguments

  * `x::AbstractArray{T} where T<:Number`: Decomposed 1D-signal.
  * `n::Integer`: Length of signal of interest.
  * `tree::BitVector`: Binary tree.
  * `redundant::Bool`: (Default: `false`) Whether the wavelet decomposition is redundant. Examples of redundant wavelet transforms are the Autocorrelation wavelet transform (ACWT), Stationary wavelet transform (SWT), and the Maximal Overlap wavelet transform (MOWT).

# Returns

`UnitRange{Integer}` or `::Tuple{UnitRange{Integer}, Integer}`: The index range of the coarsest scaling subspace based on the input binary tree.

# Examples

```@repl
using Wavelets, WaveletsExt

x = randn(8)
wt = wavelet(WT.haar)
tree = maketree(x)

# Non-redundant wavelet transform
xw = wpd(x, wt)
coarsestscalingrange(xw, tree)          # 1:1

# Redundant wavelet transform
xw = swpd(x, wt)
coarsestscalingrange(xw, tree, true)    # (1:8, 8)
```

*See also:* [`finestdetailrange`](@ref)
