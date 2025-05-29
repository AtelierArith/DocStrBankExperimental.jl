```
function quanticscrossinterpolate(
    ::Type{ValueType},
    f,
    xvals::AbstractVector{<:AbstractVector},
    initialpivots::Union{Nothing,AbstractVector{<:AbstractVector}}=nothing;
    unfoldingscheme::Symbol=:interleaved,
    nrandominitpivot=5,
    kwargs...
) where {ValueType}
```

Interpolate a function $f(\mathbf{x})$ as a quantics tensor train. This overload automatically constructs a Grid object from the $\mathbf{x}$ points given in `xvals`.

Arguments:

  * `xvals::AbstractVector{<:AbstractVector}`: A set of discrete points where `f` can be evaluated, given as a set of arrays, where `xvals[i]` describes the `i`th axis. Each array in `xvals` should contain `2^R` points for some integer `R`.
  * For all other arguments, see the documentation of the main overload.
