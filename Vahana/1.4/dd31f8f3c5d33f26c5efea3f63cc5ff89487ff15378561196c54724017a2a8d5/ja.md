```
add_edges!(sim, to::AgentID, edges)
```

シミュレーション `sim` に複数の `edges` を一度に追加します。すべてのエッジは `to` に向けられます。

`edges` はエージェントの任意の反復可能なセット、または引数としての任意の数のエッジであることができます。

[`Edge`](@ref) [`register_edgetype!`](@ref) および [`add_edge!`](@ref) も参照してください。
