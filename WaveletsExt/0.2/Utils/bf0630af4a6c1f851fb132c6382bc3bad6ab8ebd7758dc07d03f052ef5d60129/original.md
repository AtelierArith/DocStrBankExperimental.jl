```
getbasiscoefall(Xw, tree)
```

Get the basis coefficients for all decomposed signals in `Xw` with respect to the tree(s) `tree`.

# Arguments

  * `Xw::AbstractArray{T,3} where T<:Number`: A set of decomposed 1D-signals.
  * `tree::BitVector` or `tree::BitArray{2}`: The corresponding basis tree(s). If input is a `BitMatrix`, each column corresponds to a signal in `Xw`, and therefore the number of columns must be equal to the number of signals.

# Returns

  * `::Array{T,2}`: Basis coefficients of signals.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate signals and wavelet
c = ClassData(:cbf, 10, 10, 10)
X = generateclassdata(c)
wt = wavelet(WT.db4)

# Decompose signals
Xw = iwpdall(X, wt)
tree = maketree(128, 6, :dwt)

# Get basis coefficients
getbasiscoefall(Xw, tree)
```
