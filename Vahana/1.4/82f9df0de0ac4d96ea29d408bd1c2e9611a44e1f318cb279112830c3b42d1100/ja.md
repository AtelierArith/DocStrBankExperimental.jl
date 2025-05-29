```
add_edge!(sim, to::AgentID, edge::Edge{T})
```

シミュレーション `sim` に単一のエッジを追加します。エッジは、ID `edge.from` を持つエージェント（ソース）から、ID `to` を持つエージェント（ターゲット）に向かっています。

```
add_edge!(sim, from::AgentID, to::AgentID, state::T)
```

シミュレーション `sim` に単一のエッジを追加します。エッジは、ID `from` を持つエージェント（ソース）から、ID `to` を持つエージェント（ターゲット）に向かっており、状態 `state` を持っています。

`T` は、[`register_edgetype!`](@ref) を呼び出すことによって、事前にシミュレーションに登録されている必要があります。

他にも [`Edge`](@ref) [`register_edgetype!`](@ref) および [`add_edges!`](@ref) を参照してください。
