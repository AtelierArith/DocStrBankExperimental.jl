```
RangeMatrix(rs::AbstractVector{T}) where T <: AbstractRange
```

A RangeMatrix is a simple matrix representation of a vector of ranges, with each range representing one column. Construct a RangeMatrix with a vector of ranges; the ranges must all have the same length.

Note that it is only efficient when all the ranges are of the same type and in a concretely typed Vector.
