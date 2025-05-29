```
distance(u::MGPoint, v::MGPoint) -> Float64
distance(s::Segment) -> Float64
distance(coords::AbstractMatrix{T}) where {T<:Real} -> Float64
```

Return distance between two endpoints.
