```
ideal_class_monoid(R::AbsNumFieldOrder)
  -> Vector{FacElem{AbsSimpleNumFieldOrderFractionalIdeal, AbsNumFieldOrderFractionalIdealSet{AbsSimpleNumField, AbsSimpleNumFieldElem}}}
ideal_class_monoid(R::AlgAssAbsOrd)
  -> Vector{FacElem{AlgAssAbsOrdIdl, AlgAssAbsOrdIdlSet}}
```

Given an order $R$ in a number field or a finite product of number fields, this function returns representatives of the isomorphism classes of fractional ideals in $R$.
