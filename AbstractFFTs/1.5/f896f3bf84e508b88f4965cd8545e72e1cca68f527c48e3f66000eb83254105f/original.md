```
(p::Plan)'
adjoint(p::Plan)
```

Return a plan that performs the adjoint operation of the original plan.

!!! warning
    Adjoint plans do not currently support `LinearAlgebra.mul!`. Further, as a new addition to `AbstractFFTs`,  coverage of `Base.adjoint` in downstream implementations may be limited.

