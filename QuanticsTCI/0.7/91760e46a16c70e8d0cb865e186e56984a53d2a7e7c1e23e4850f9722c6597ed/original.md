```
function quanticscrossinterpolate(
    ::Type{ValueType},
    f,
    xvals::AbstractVector,
    initialpivots::AbstractVector=[1];
    kwargs...
) where {ValueType}
```

Interpolate a function $f(x)$ as a quantics tensor train. This is an overload for 1d functions. For an explanation of arguments and return type, see the documentation of the main overload.
