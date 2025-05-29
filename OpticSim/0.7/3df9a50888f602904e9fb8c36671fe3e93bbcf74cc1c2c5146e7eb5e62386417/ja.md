```
Triangle{T} <: Surface{T}
```

三角形の表面であり、有効なCSGオブジェクトではありません。主に[`TriangleMesh`](@ref)の構成要素として使用されるか、[`AcceleratedParametricSurface`](@ref)の交差を可能にするために使用されます。[`OpticalInterface`](@ref)を持たないため、光学表面として直接使用することはできません。

```julia
Triangle(v1::SVector{3,T}, v2::SVector{3,T}, v3::SVector{3,T}, [uv1::SVector{2,T}, uv2::SVector{2,T}, uv3::SVector{2,T}])
```
