```
boundary_point(p1::T, p2::T, bounds::Bounds{T}) where T<:Union{LLA,ENU}
```

境界内の最も近い点を見つけます。これは、inbounds(p1) != inbounds(p2) の場合にのみ機能します。
