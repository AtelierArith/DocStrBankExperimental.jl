```
adjoint(A::LinearMap)
```

Construct a lazy representation of the adjoint of `A`. This can be either a `AdjointMap` wrapper of `A`, or a suitably redefined instance of the same type as `A`. For instance, for a linear combination of linear maps $A + B$, the adjoint is given by $A^* + B^*$, i.e., another linear combination of linear maps.
