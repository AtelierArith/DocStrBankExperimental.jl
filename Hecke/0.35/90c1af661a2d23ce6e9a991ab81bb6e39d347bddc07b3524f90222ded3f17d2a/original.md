```
restrict_scalars(A::StructureConstantAlgebra{AbsSimpleNumFieldElem}, KtoL::NumFieldHom{AbsSimpleNumField, AbsSimpleNumField})
  -> StructureConstantAlgebra, Map
```

Given an algebra $A$ over a number field $L$ and an inclusion map `KtoL` from a number field $K$ to $L$, this function returns the restriction $B$ of $A$ to $K$ and the morphism $B \to A$.
