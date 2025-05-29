```
add_edge_dataset!(dg::D, weight_dict, attribute) where {D <: DataGraphUnion}
```

`weight_dict`のデータを`dg`の`attribute`という名前のエッジデータとして追加します。`weight_dict`は、`dg.edges`のエッジに対応するキー（整数ではなくノード名）を含む必要があります。
