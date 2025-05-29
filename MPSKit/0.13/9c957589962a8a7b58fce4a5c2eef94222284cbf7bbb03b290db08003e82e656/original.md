```
WindowArray{T} <: AbstractVector{T}
```

A vector embedded in a periodic environment to the left and right, which can be accessed with arbitrary integer indices. The `middle` part is a regular `Vector{T}` and the `left` and `right` parts are `PeriodicVector{T}`s.

This vector inherits most of its properties from the middle part, including its length and axes. Nevertheless, indexing operations are overloaded to allow for out-of-bounds access, which is resolved by the periodic enviroments.

See also [`PeriodicVector`](@ref).
