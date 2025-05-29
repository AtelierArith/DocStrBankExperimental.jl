```
get_graphelement(c::EdgeModel)::@NamedTuple{src::T, dst::T}
get_graphelement(c::VertexModel)::Int
get_graphelement(nw::Network, idx::Union{VIndex,EIndex})
```

コンポーネントモデルの `graphelement` メタデータを取得します。エッジの場合、これは名前付きタプル `(;src, dst)` を返し、両方は整数（頂点インデックス）またはシンボル（頂点名）です。
