```
scalartype(x)
```

Returns the type of scalar over which the vector-like object `x` behaves as a vector, e.g. the type of scalars with which `x` could be scaled in-place. This function should also work in the type domain, i.e. if `x` is a vector like object, then also `scalartype(typeof(x))` should work.

!!! note
    New types should only implement the method with the argument in the type domain.

