```
Model(::Type{T}, f::Union{Nothing, Function}) where {T}
```

Constructs an empty model with objective function `f` and decision variable value type `Vector{T}`. `f` can be an instance of `Base.Function` but must return a number,  or it can be an intance of [`Objective`](@ref). `f` can also be `nothing` in which case, the objective function can be defined later using [`set_objective!`](@ref).
