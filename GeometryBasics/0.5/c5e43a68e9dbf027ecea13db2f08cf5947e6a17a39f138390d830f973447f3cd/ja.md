```
uv_normal_mesh(primitive::GeometryPrimitive{N}[; pointtype = Point{N, Float32}, facetype = GLTriangleFace, uvtype = Vec2f, normaltype = Vec3f])
```

与えられた `primitive` からテクスチャ座標と法線を持つ三角形メッシュを作成します。`pointtype`、`facetype`、`uvtype`、および `normaltype` は、対応するキーワード引数によって設定されます。

関連情報: [`triangle_mesh`](@ref)、[`normal_mesh`](@ref)、[`uv_mesh`](@ref)、[`uv_normal_mesh`](@ref)
