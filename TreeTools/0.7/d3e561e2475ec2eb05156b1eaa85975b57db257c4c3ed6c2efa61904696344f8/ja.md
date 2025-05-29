```
traversal([f], tree, style=:postorder; internals, leaves, root)
traversal([f], node, style=:postorder; internals, leaves, root)
```

`style` に従って `tree` のノードを反復処理し、`f` が `false` を返すノードはスキップします。`style` は `collect(keys(TreeTools.traversal_styles))` に含まれている必要があります。現時点では `:postorder` のみです。

詳細なドキュメントは `postorder_traversal` を参照してください。
