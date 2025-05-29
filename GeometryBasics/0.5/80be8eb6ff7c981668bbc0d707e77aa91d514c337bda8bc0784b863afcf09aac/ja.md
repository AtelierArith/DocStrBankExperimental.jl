```
uv_mesh(primitive::GeometryPrimitive{N}[; pointtype = Point{N, Float32}, facetype = GLTriangleFace, uvtype = Vec2f])
```

与えられた `primitive` からテクスチャ座標を持つ三角形メッシュを作成します。 `pointtype`、`facetype`、および `uvtype` は、対応するキーワード引数によって設定されます。

参照: [`triangle_mesh`](@ref), [`normal_mesh`](@ref), [`uv_mesh`](@ref), [`uv_normal_mesh`](@ref)
