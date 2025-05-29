```
transpose(A::LinearMap)
```

Construct a lazy representation of the transpose of `A`. This can be either a `TransposeMap` wrapper of `A`, or a suitably redefined instance of the same type as `A`. For instance, for a linear combination of linear maps $A + B$, the transpose is given by $A^⊤ + B^⊤$, i.e., another linear combination of linear maps.
