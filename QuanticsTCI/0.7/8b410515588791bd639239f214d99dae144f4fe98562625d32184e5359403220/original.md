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

Interpolate a function $f(\mathbf{x})$ as a quantics tensor train. This overload automatically constructs a Grid object using the information contained in `size`. Here, the `i`th argument runs from `1` to `size[i]`.
