```
axpy!(a::Real, x::CeedVector, y::CeedVector)
```

Overwrite `y` with `x*a + y`, where `a` is a scalar. Returns `y`.

!!! warning "Different argument order"
    In order to be consistent with `LinearAlgebra.axpy!`, the arguments are passed in order: `a`, `x`, `y`. This is different than the order of arguments of the C function `CeedVectorAXPY`.

