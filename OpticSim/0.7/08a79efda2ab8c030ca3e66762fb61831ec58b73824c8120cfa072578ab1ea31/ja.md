```
point(ray::AbstractRay{T,N}, alpha::T) -> SVector{T, N}
```

原点 + alpha * 方向のレイ上の点を返します。Alpha は >= 0 でなければなりません。
