```
normal_mesh(primitive::GeometryPrimitive{N}[; pointtype = Point{N, Float32}, facetype = GLTriangleFace, normaltype = Vec3f])
```

Creates a triangle mesh with normals from a given `primitive`. The `pointtype`, `facetype` and `uvtype` and `normaltype` are set by the corresponding keyword arguments.

See also: [`triangle_mesh`](@ref), [`normal_mesh`](@ref), [`uv_mesh`](@ref), [`uv_normal_mesh`](@ref)
