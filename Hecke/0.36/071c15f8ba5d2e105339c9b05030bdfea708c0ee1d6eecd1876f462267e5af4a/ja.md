```
direct_product(fields::AnticNumberFields...)
  -> StructureConstantAlgebra{QQFieldElem}, Vector{AbsAlgAssToNfAbsMor}
direct_product(fields::Vector{AnticNumberFields})
  -> StructureConstantAlgebra{QQFieldElem}, Vector{AbsAlgAssToNfAbsMor}
```

代数 $A = K_1 \times \cdots \times K_k$ と射影写像 $A ->> K_i$ を返します。
