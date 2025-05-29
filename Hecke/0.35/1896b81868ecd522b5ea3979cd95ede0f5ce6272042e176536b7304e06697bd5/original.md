```
factor_coprime(Q::FacElem{AbsSimpleNumFieldOrderFractionalIdeal, AbsNumFieldOrderFractionalIdealSet{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> Dict{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}
```

A coprime factorisation of $Q$: each ideal in $Q$ is split using \code{integral_split} and then a coprime basis is computed. This does {\bf not} use any factorisation.
