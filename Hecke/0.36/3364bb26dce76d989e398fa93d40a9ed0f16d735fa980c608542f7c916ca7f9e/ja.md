```
restrict_scalars(A::AbstractAssociativeAlgebra{AbsSimpleNumFieldElem}, Q::QQField)
restrict_scalars(A::AbstractAssociativeAlgebra{fqPolyRepFieldElem}, Fp::fpField)
restrict_scalars(A::AbstractAssociativeAlgebra{FqPolyRepFieldElem}, Fp::EuclideanRingResidueField{ZZRingElem})
  -> StructureConstantAlgebra, Function, Function
```

与えられた代数 $A$ が体 $L$ 上にあり、$L$ の素体 $K$ があるとき、この関数は $A$ の $K$ への制限 $B$ を返し、$A$ から $B$ へのマッピングと $B$ から $A$ へのマッピングを提供します。
