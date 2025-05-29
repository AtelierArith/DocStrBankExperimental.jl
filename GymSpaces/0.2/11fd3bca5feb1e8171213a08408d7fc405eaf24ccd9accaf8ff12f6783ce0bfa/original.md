```
Box(low::Number, high::Number, shape::Union{Tuple, Array{<:Integer, 1}}, dtype::Union{DataType, Nothing}=nothing; seed::Int=42)
```

A box in R^n with a low and high values of being vectors of `low` and `high` and of shape `shape`. Optional input `seed` for sampling.

Example Box(-1.0, 1.0, (3,4)) # low and high are scalars, and shape is provided
