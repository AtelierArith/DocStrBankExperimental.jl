```
Triangle{T} <: Surface{T}
```

Triangular surface, not a valid CSG object. Primarily used as a component part of [`TriangleMesh`](@ref) or to enable intersection of [`AcceleratedParametricSurface`](@ref)s. Can never be used directly as an optical surface as it doesn't have an [`OpticalInterface`](@ref).

```julia
Triangle(v1::SVector{3,T}, v2::SVector{3,T}, v3::SVector{3,T}, [uv1::SVector{2,T}, uv2::SVector{2,T}, uv3::SVector{2,T}])
```
