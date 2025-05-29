```
getbasiscoef(Xw, tree)
```

Get the basis coefficients for the decomposed signal `Xw` with respect to the tree `tree`.

# Arguments

  * `Xw::AbstractArray{T,2} where T<:Number`: Decomposed 1D-signal.
  * `tree::BitVector`: The corresponding basis tree.

# Returns

  * `::Array{T,1}`: Basis coefficients of signal.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate signal and wavelet
x = generatesignals(:heavysine)
wt = wavelet(WT.db4)

# Decompose signal
Xw = iwpd(x, wt)
tree = maketree(128, 6, :dwt)

# Get basis coefficients
xw = getbasiscoef(Xw, tree)
```
