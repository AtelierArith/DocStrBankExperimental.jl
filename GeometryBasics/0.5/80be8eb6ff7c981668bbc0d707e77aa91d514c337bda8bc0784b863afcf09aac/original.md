```
uv_mesh(primitive::GeometryPrimitive{N}[; pointtype = Point{N, Float32}, facetype = GLTriangleFace, uvtype = Vec2f])
```

Creates a triangle mesh with texture coordinates from a given `primitive`. The `pointtype`, `facetype` and `uvtype` are set by the corresponding keyword arguments.

See also: [`triangle_mesh`](@ref), [`normal_mesh`](@ref), [`uv_mesh`](@ref), [`uv_normal_mesh`](@ref)
