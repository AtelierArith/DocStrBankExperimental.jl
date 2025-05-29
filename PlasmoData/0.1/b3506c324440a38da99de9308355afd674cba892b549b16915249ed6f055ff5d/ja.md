```
add_node_attribute!(datagraph, attribute, default_weight = 0.0)
add_node_attribute!(datadigraph, attribute, default_weight = 0.0)
```

`node_data` 行列に `attribute` という名前の列を `default_weight` で埋めます。もし `attribute` がすでにノードデータに存在する場合は、エラーが発生します。
