```
direct_product(fields::AnticNumberFields...)
  -> StructureConstantAlgebra{QQFieldElem}, Vector{AbsAlgAssToNfAbsMor}
direct_product(fields::Vector{AnticNumberFields})
  -> StructureConstantAlgebra{QQFieldElem}, Vector{AbsAlgAssToNfAbsMor}
```

Returns the algebra $A = K_1 \times \cdots \times K_k$ and the projection maps $A ->> K_i$.
