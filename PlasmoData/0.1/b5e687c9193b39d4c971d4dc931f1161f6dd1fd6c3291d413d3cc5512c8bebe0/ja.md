```
add_edge_dataset!(dg::D, edge_list, weight_list, attribute) where {D <: DataGraphUnion}
```

`weight_list`のエッジデータを`dg`に追加します。`edge_list`は`dg`内のエッジのリスト（整数ではなくノード名）であり、`weight_list`は`attribute`の名前の下にエッジデータとして保存されるデータ/オブジェクトのリストです。`edge_list`と`weight_list`は同じ長さでなければならず、`weight_list`のエントリは`edge_list`の対応するエッジに追加されます。
