```
rename_node_attribute!(dg::D, attribute, new_name) where {D <: DataGraphUnion}
```

ノードデータ `attribute` を `new_name` に名前変更します。`attribute` が定義されていない場合、エラーを返します。
