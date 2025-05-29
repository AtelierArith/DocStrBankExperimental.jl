```
add_edge_dataset!(dg::D, weight_list, attribute) where {D <: DataGraphUnion}
```

`weight_list`のエントリを`dg`の`attribute`という名前のエッジデータとして追加します。`weight_list`は`dg`のエッジの数と同じ長さでなければなりません。`weight_list`のエントリは、`dg.edges`にリストされているエッジの順序でエッジデータとして追加されます。
