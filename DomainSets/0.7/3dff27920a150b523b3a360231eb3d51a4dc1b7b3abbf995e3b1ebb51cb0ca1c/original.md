```
DynamicUnitBall(dim::Int)
DynamicUnitBall{T}(dim::Int)
DynamicUnitBall{T,C=:closed}(dim::Int)
```

The open or closed unit ball with variable dimension. Typically the element type is a `Vector{T}` and `dim` specifies the length of the vectors.
