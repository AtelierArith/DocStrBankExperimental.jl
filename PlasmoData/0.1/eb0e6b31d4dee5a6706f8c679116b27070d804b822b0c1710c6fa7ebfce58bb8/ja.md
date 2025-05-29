```
add_node_dataset!(dg::D, weight_list, attribute) where {D <: DataGraphUnion}
```

`weight_list`のエントリを`dg`の`attribute`という名前のノードデータとして追加します。`weight_list`は`dg`のノード数と同じ長さでなければなりません。`weight_list`のエントリは、`dg.nodes`にリストされているノードの順序でノードデータとして追加されます。
