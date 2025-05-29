```
^(f::TorQuadModuleMap, n::Integer) -> TorQuadModuleMap
```

Given an abelian group endomorphism `f` of a torsion quadratic module `T` return the $n$-fold self-composition of `f`.

Note that `n` must be non-negative and $f^0$ is by default the identity map of the domain of `f` (see [`identity_map`](@ref)).
