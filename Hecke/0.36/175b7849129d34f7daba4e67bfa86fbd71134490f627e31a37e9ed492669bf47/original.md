```
norm(m::T, a::AbsSimpleNumFieldElem) where T <: Map{AbsSimpleNumField, AbsSimpleNumField} -> AbsSimpleNumFieldElem
```

Given an embedding $m:k\to K$ of number fields and an element in $K$, find the norm $N_{K/k}(a)$.
