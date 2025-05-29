```
simplify(x::FacElem{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, AbsNumFieldOrderIdealSet{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> FacElem
simplify(x::FacElem{AbsSimpleNumFieldOrderFractionalIdeal, AbsNumFieldOrderFractionalIdealSet{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> FacElem
```

Uses `coprime_base` to obtain a simplified version of $x$, ie. in the simplified version all base ideals will be pariwise coprime but not necessarily prime!.
