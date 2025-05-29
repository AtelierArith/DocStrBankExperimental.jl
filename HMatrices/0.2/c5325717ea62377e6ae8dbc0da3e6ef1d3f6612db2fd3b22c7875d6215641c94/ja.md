```
ClusterTree(elements,splitter;[copy_elements=true, threads=false])
```

与えられた `elements` から、`splitter` にエンコードされた分割戦略を使用して `ClusterTree` を構築します。`copy_elements` が false に設定されている場合、`elements` 引数は `ClusterTree` に直接保存され、ツリー構築中に順序が変更されます。
