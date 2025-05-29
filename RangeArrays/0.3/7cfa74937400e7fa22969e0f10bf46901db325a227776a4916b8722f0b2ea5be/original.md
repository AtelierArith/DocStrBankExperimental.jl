```
RepeatedRangeMatrix(r::AbstractRange{T}, at::AbstractVector{T}) where T
```

A RepeatedRange is like a RangeMatrix, except that it only stores one range and a vector of offsets, at which the range repeats. For now, both the range and vector of offsets must have the same element type.
