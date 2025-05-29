```
write_solution(vtk::VTKGridFile, dh::AbstractDofHandler, u::AbstractVector, suffix="")
```

自由度ベクトル `u` のノードの値を `vtk` に保存します。 `dh` の各フィールドは別々に保存され、`suffix` はフィールド名に追加するために使用できます。

`u` はテンソル値を含むこともできますが、`u` の各エントリは `dh` の自由度に対応する必要があります。詳細については [`write_node_data`](@ref write_node_data) を参照してください。グリッド内のノードによってすでにソートされている値をエクスポートする場合は、`write_node_data` を直接使用してください。
