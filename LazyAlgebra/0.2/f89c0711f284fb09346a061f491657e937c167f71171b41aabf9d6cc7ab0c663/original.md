```
Diag(A) -> NonuniformScaling(A)
```

yields a non-uniform scaling linear mapping (of type `NonuniformScaling`) whose effect is to apply elementwise multiplication of its argument by the scaling factors `A`.  This mapping can be thought as a *diagonal* operator.

The `diag` method in `LinearAlgebra` can be called to retrieve the scaling factors:

```
using LinearAlgebra
W = Diag(A)
diag(W) === A  # this is true
```

!!! note
    Beware of the differences between the [`Diag`](@ref) (with an uppercase 'D') and [`diag`](@ref) (with an lowercase 'd') methods.

