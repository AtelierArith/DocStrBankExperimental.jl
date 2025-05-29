```
function quanticscrossinterpolate(
    ::Type{ValueType},
    f,
    size::NTuple{d,Int},
    initialpivots::AbstractVector{<:AbstractVector}=[ones(Int, d)];
    unfoldingscheme::Symbol=:interleaved,
    kwargs...
) where {ValueType,d}
```

Interpolate a Tensor $F$ as a quantics tensor train. For an explanation of arguments, etc., see the documentation of the main overload.
