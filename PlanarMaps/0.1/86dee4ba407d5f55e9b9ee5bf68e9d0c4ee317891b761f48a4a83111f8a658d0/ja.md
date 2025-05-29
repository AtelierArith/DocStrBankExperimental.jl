```
add_edge!(P::PlanarMap,i::Integer,j::Integer,F::Face)
add_edge!(P::PlanarMap,i::Integer,j::Integer)
```

平面マップ `P` において、`i` から `j` へのエッジを面 `F` を通じて追加します。`F` が指定されていない場合、`i` の `NeighborCycle` で最初に発見された面が使用されます。
