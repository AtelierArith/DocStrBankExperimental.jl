```
partial_copy(pso::PSOModel{T, U};
    Y::Union{Vector{V}, Nothing}=nothing,
    P::Union{V, Nothing}=nothing,
    Q::Union{V, Nothing}=nothing,
    ports::Union{AbstractVector{W}, Nothing}=nothing) where {T, U, V, W}

partial_copy(bbox::Blackbox{T, U};
    Y::Union{Vector{V}, Nothing}=nothing,
    P::Union{V, Nothing}=nothing,
    Q::Union{V, Nothing}=nothing,
    ports::Union{AbstractVector{W}, Nothing}=nothing) where {T, U, V, W}
```

Create a new model with the same fields except those given as keyword arguments.
