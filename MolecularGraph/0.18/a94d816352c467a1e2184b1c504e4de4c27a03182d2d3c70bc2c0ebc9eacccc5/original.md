```
unitvector(u::MGPoint, v::MGPoint) -> MGPoint
unitvector(s::Segment) -> MGPoint
unitvector(coords::AbstractMatrix{T}) where {T<:Real} -> AbstractMatrix
```

Return u -> v vector of length 1.
