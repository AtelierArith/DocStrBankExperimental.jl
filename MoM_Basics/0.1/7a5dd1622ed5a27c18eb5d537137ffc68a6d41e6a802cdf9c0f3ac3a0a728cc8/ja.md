```
dist(pa::AbstractVector{FT}, pb::AbstractVector{FT})::FT where {FT<:AbstractFloat}
dist(pa::Vec3D{FT}, pb::Vec3D{FT})::FT where {FT<:AbstractFloat}
dist(pa::Vec3D{FT})::FT where {FT<:AbstractFloat}
```

2点間の距離を計算します。norm関数を使用するよりも効率的です。
