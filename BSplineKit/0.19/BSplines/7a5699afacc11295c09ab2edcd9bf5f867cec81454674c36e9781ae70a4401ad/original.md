```
static_length(::Type{<:AbstractBSplineBasis}) -> Union{Int, Nothing}
static_length(::AbstractBSplineBasis) -> Union{Int, Nothing}
```

Return the basis' length if it is statically known (i.e. at compile time); return `nothing` otherwise.

Typically, bases with statically-known length are those constructed using an `SVector` (from the StaticArrays package) to describe the basis breakpoints.
