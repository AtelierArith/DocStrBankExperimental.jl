```
GeneralizedPCAcor(X::AbstractMatrix{T};
                  num_components::Union{Int, Nothing}=nothing,
                  vmin::Union{T, Nothing}=nothing,
                  rtol::Union{T, Nothing}=nothing) where {T<:Base.IEEEFloat}
```

Construct a generalized PCAcor transformer from the `q × n` matrix, each row of which is a sample of an `n`-dimensional random variable.
