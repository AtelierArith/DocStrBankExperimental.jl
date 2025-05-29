```
permute(f::FusionTree, p::NTuple{N, Int}) -> <:AbstractDict{typeof(t), <:Number}
```

Perform a permutation of the uncoupled indices of the fusion tree `f` and returns the result as a `<:AbstractDict` of output trees and corresponding coefficients; this requires that `BraidingStyle(sectortype(f)) isa SymmetricBraiding`.
