```
braid(f::FusionTree{<:Sector, N}, levels::NTuple{N, Int}, p::NTuple{N, Int})
-> <:AbstractDict{typeof(t), <:Number}
```

Perform a braiding of the uncoupled indices of the fusion tree `f` and return the result as a `<:AbstractDict` of output trees and corresponding coefficients. The braiding is determined by specifying that the new sector at position `k` corresponds to the sector that was originally at the position `i = p[k]`, and assigning to every index `i` of the original fusion tree a distinct level or depth `levels[i]`. This permutation is then decomposed into elementary swaps between neighbouring indices, where the swaps are applied as braids such that if `i` and `j` cross, $τ_{i,j}$ is applied if `levels[i] < levels[j]` and $τ_{j,i}^{-1}$ if `levels[i] > levels[j]`. This does not allow to encode the most general braid, but a general braid can be obtained by combining such operations.
