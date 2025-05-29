```
components(A::GridArray{T})
```

Splits `A` into a tuple of `GridArray`s where there is one for each component of `T`.

Note, the data for the components is shared with the original array.

For example, if `A isa GridArray{SVector{3, Float64}}` then a tuple of type `NTuple{3, GridArray{Float64}}` would be returned.
