```julia
next_inconsistent_idx(
    arg,
    idx,
    stack;
    mutations_edges,
    buffer
)

```

次の不整合マーカーのインデックス、すなわち、与えられた祖先再結合グラフにおいて二回以上変異する次のマーカーです。

`stack` は `CheapStack{Edge{VertexType}}` 型でなければなりません（[`CheapStack`](@ref)を参照）。
