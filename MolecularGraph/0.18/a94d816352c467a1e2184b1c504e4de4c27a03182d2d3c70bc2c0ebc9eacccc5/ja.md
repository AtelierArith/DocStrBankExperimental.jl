```
unitvector(u::MGPoint, v::MGPoint) -> MGPoint
unitvector(s::Segment) -> MGPoint
unitvector(coords::AbstractMatrix{T}) where {T<:Real} -> AbstractMatrix
```

長さ1のu -> vベクトルを返します。
