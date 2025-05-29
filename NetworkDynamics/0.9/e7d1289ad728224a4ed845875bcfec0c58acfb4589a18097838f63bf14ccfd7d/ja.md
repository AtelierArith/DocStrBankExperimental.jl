```
get_marker(v::VertexModel)
get_marker(nw::Network, vidx::VIndex)
```

頂点 `v` の `marker` メタデータを返します。存在しない場合はエラーが発生する可能性があります。

関連情報: [`has_marker`](@ref), [`set_marker!`](@ref).
