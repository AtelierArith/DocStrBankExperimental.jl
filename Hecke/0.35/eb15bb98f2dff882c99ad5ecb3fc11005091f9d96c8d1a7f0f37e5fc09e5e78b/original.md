```
*(a::IntegerUnion, f::TorQuadModuleMap) -> TorQuadModuleMap
*(f::TorQuadModuleMap, a::IntegerUnion) -> TorQuadModuleMap
```

Given an abelian group homomorphism `f` between two torsion quadratic modules `T` and `U`, return the pointwise $a$-twist morphism `h` of `f` which sends every element `b` of `T` to $h(b) := a*f(b)$.
