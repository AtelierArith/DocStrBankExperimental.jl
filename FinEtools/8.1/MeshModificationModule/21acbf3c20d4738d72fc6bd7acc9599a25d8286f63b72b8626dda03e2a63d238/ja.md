```
fusenodes(fens1::FENodeSet{T}, fens2::FENodeSet{T}, tolerance::T) where {T<:Number}
```

2つのノードセットからノードを結合します。

2つのノードセットを結合します。必要に応じて、互いに許容範囲内にあるノードを接着することによって。2つのノードセット、`fens1` と `fens2` は、`tolerance` のサイズのボックス内にあるノードをマージすることによって結合されます。マージされたノードセット `fens` と、セット `fens1` 内のノードの新しいインデックスが返されます。

セット `fens2` は、変更されずに同じ順序でノードセット `fens` に含まれます。ノードセット `fens1` のインデックスは変更されます。

# 例

この関数の呼び出し後、`k=new_indexes_of_fens1_nodes[j]` は、ノードセット `fens` 内のノードであり、以前はノードセット `fens1` のノード `j` でした。以前 `fens1` を参照していた有限要素セットの接続は、同じノードをセット `fens` 内で参照するように更新する必要があります。`updateconn!(fes, new_indexes_of_fens1_nodes);`
