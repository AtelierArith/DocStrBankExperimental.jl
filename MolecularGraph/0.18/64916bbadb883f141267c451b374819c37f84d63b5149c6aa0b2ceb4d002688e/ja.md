```
distance(u::MGPoint, v::MGPoint) -> Float64
distance(s::Segment) -> Float64
distance(coords::AbstractMatrix{T}) where {T<:Real} -> Float64
```

2つの端点間の距離を返します。
