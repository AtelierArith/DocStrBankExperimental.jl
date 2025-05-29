```
ispolynomial(s::AbstractSystem)
```

Determines whether the dynamics of system `s` is specified by polynomial equations.

The result of this function only depends on the system type, not the value, and can also be applied to `typeof(s)`. Hence, e.g. a `LinearContinuousSystem` is not considered to be of polynomial type.
