```
coprime_base(A::Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}
coprime_base(A::Vector{AbsSimpleNumFieldOrderElem}) -> Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}
```

A coprime base for the (principal) ideals in $A$, i.e. the returned array generated multiplicatively the same ideals as the input and are pairwise coprime.
