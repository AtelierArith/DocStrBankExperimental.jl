```
dist(pa::AbstractVector{FT}, pb::AbstractVector{FT})::FT where {FT<:AbstractFloat}
dist(pa::Vec3D{FT}, pb::Vec3D{FT})::FT where {FT<:AbstractFloat}
dist(pa::Vec3D{FT})::FT where {FT<:AbstractFloat}
```

计算两点之间距离，比使用norm函数更高效。
