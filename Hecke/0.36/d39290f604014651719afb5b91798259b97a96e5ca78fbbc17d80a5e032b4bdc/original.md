```
minimum(m::T, I::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) where T <: Map{AbsSimpleNumField, AbsSimpleNumField} -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}
```

Given an embedding $m:k\to K$ of number fields and an integral ideal in $K$, find the intersect $I \cap \mathbf{Z}_k$.
