```
coefficient(v1::VariableRef, v2::VariableRef)
```

Return `1.0` if `v1 == v2`, and `0.0` otherwise.

This is a fallback for other [`coefficient`](@ref) methods to simplify code in which the expression may be a single variable.
