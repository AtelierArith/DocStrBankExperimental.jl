```
midpoint(u::MGPoint, v::MGPoint) -> MGPoint
midpoint(s::Segment) -> MGPoint
midpoint(coords::AbstractMatrix{T}) where {T<:Real} -> AbstractMatrix
```

Return the midpoint of u and v.
