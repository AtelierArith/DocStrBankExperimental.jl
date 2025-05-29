```
restrict_scalars(A::StructureConstantAlgebra{AbsSimpleNumFieldElem}, KtoL::NumFieldHom{AbsSimpleNumField, AbsSimpleNumField})
  -> StructureConstantAlgebra, Map
```

数体 $L$ 上の代数 $A$ と、数体 $K$ から $L$ への包含写像 `KtoL` が与えられたとき、この関数は $A$ の $K$ への制限 $B$ と、$B \to A$ の写像を返します。
