```
uv(surf::ParametricSurface{T}, p::SVector{3,T}) -> SVector{2,T}
uv(surf::ParametricSurface{T}, x::T, y::T, z::T) -> SVector{2,T}
```

Returns the uv coordinate on `surf` of a point, `p`, in 3D space. If `onsurface(surf, p)` is false then the behavior is undefined, it may return an inorrect uv, an invalid uv, NaN or crash.
