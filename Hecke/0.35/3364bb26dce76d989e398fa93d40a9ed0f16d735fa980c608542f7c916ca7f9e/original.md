```
restrict_scalars(A::AbstractAssociativeAlgebra{AbsSimpleNumFieldElem}, Q::QQField)
restrict_scalars(A::AbstractAssociativeAlgebra{fqPolyRepFieldElem}, Fp::fpField)
restrict_scalars(A::AbstractAssociativeAlgebra{FqPolyRepFieldElem}, Fp::EuclideanRingResidueField{ZZRingElem})
  -> StructureConstantAlgebra, Function, Function
```

Given an algebra $A$ over a field $L$ and the prime field $K$ of $L$, this function returns the restriction $B$ of $A$ to $K$ and maps from $A$ to $B$ and from $B$ to $A$.
