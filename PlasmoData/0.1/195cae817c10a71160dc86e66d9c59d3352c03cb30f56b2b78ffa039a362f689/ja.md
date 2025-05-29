```
add_edge_attribute!(datagraph, attribute, default_weight = 0.0)
add_edge_attribute!(datadigraph, attribute, default_weight = 0.0)
```

`edge_data` 行列に `attribute` という名前の `default_weight` で満たされた列を追加します。もし `attribute` がすでにエッジデータに存在する場合は、エラーが発生します。
