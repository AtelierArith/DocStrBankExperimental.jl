```
function export_vtf(file::AbstractString, pge::PeriodicGraphEmbedding3D{T}, types=nothing, repeatedges=6, colorname=false, tostring=string, atomnumof==(a,i)->(a isa Integer ? a : i)) where T
```

[`PeriodicGraphEmbedding3D`](@ref) を .vtf `file` にエクスポートします（VMDで読み取り可能）。

指定されている場合、`types` は `pge` の各頂点のタイプのリストです。各タイプは `tostring` 関数によって文字列に変換されます。`atomnumof` 関数は二つの引数 `ty` と `i` を取り、`ty` はタイプ、`i` は頂点の番号であり、原子番号を表す `Int` を返します。
