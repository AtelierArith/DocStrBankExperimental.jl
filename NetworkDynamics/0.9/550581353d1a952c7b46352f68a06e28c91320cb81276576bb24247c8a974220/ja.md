```
set_graphelement!(c::EdgeModel, nt::@NamedTuple{src::T, dst::T})
set_graphelement!(c::EdgeModel, p::Pair)
set_graphelement!(c::VertexModel, vidx::Int)
set_graphelement!(nw::Network, idx::Union{VIndex,EIndex}, value)
```

コンポーネントの `graphelement` メタデータを設定します。エッジの場合、これは名前付きタプル `(;src, dst)` を取り、両方は整数（頂点インデックス）またはシンボル（頂点名）である必要があります。頂点の場合は、単一の整数 `vidx` を取ります。
