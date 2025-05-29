```
add_edge!(meta_graph, label_1, label_2, data)
```

MetaGraph `meta_graph` にメタデータ `data` を持つエッジ `(label_1, label_2)` を追加します。`meta_graph` の `EdgeData` 型が `Nothing` の場合、`data` は省略可能です。

エッジが追加された場合は `true` を返し、そうでない場合は `false` を返します。ラベルのいずれかが存在しない場合、何も起こらず `false` が返されます（ラベルは挿入されません）。`(label_1, label_2)` がすでに存在する場合、そのデータは `data` に更新されますが、それでも `false` が返されます。
