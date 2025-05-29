```
bestbasistree!(siwtObj)
```

Computes the best basis tree of an SIWT object and discards all nodes that are not part of the best basis tree.

# Arguments

  * `siwtObj::ShiftInvariantWaveletTransformObject{N,T₁,T₂} where {N, T₁<:Integer, T₂<:AbstractFloat}`: SIWT object.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SIWPD
siwtObj = siwpd(x, wt)

# Best basis tree
bestbasistree!(siwtObj)
```

**See also:** [`bestbasis_treeselection!`](@ref), [`isvalidtree`](@ref)
