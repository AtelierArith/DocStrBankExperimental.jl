```
get_position(v::VertexModel)
get_position(nw::Network, vidx::VIndex)
```

頂点 `v` の `position` メタデータを返します。存在しない場合はエラーが発生する可能性があります。

関連情報: [`has_position`](@ref), [`set_position!`](@ref).
