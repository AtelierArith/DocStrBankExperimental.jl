```
boundary_point(p1::T, p2::T, bounds::Bounds{T}) where T<:Union{LLA,ENU}
```

Find the closest point within bounds Works only for points where inbounds(p1) != inbounds(p2)
