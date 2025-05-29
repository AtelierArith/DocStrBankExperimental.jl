```
scalartype(op::AbstractObservable)
```

Return the type of the underlying scalar field of the operator. This may be different from the element type of the operator returned by [`eltype`](@ref), which can be a vector value.

Part of the [`AbstractObservable`](@ref) interface.

!!! note
    New types do not have to implement this method explicitly. An implementation is provided based on the [`AbstractObservable`](@ref)'s type parameter.

