```
add_node_dataset!(dg::D, weight_dict, attribute) where {D <: DataGraphUnion}
```

`weight_dict`のデータを`dg`の`attribute`という名前のノードデータとして追加します。`weight_dict`は`dg.nodes`のノード名に対応するキーを含む必要があります。
