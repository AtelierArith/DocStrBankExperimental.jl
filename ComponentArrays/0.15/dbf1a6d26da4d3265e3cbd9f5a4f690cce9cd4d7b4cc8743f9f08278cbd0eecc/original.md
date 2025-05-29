```
x = ComponentVector(nt::NamedTuple)
x = ComponentVector(;kwargs...)
x = ComponentVector(data::AbstractVector, ax)
x = ComponentVector{T}(args...; kwargs...) where T
```

A `ComponentVector` is an alias for a one-dimensional `ComponentArray`.
