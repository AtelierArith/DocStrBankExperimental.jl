```
midpoint(u::MGPoint, v::MGPoint) -> MGPoint
midpoint(s::Segment) -> MGPoint
midpoint(coords::AbstractMatrix{T}) where {T<:Real} -> AbstractMatrix
```

uとvの中点を返します。
