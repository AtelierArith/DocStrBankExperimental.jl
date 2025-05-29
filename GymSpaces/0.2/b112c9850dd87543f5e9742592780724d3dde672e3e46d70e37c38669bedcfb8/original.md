```
Box(low::Number, high::Number, shape::Union{Tuple, Array{<:Integer, 1}}, dtype::Union{DataType, Nothing}=nothing; seed::Int=42)
```

A box in R^n, i.e., each coordinate is bounded.

Two kinds of valid input:     Box(-1.0, 1.0, (3,4)) # low and high are scalars, and shape is provided     Box([-1.0,-2.0], [2.0,4.0]) # low and high are arrays of the same shape
