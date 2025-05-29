```
ideal_class_monoid(R::AbsNumFieldOrder)
  -> Vector{FacElem{AbsSimpleNumFieldOrderFractionalIdeal, AbsNumFieldOrderFractionalIdealSet{AbsSimpleNumField, AbsSimpleNumFieldElem}}}
ideal_class_monoid(R::AlgAssAbsOrd)
  -> Vector{FacElem{AlgAssAbsOrdIdl, AlgAssAbsOrdIdlSet}}
```

数体の位数 $R$ または数体の有限積に対して、この関数は $R$ の分数イデアルの同型類の代表を返します。
