```
postorder_traversal([f], tree; root=true, leaves=true, internals=true)
```

`tree`を後順で走査し、ノードを反復処理します。`node`の子は`children(node)`と同じ順序で返されます。

`f(n)`が真であるノード`n`のみを保持します。`leaves`、`internals`、または`root`が`false`に設定されている場合、対応するノードは除外されます。

## 例

```julia
for node in postorder_traversal(tree; root=false)
    isroot(node) # 常にfalse
end

[label(x) for x in postorder_traversal(tree; internals=false)] # 葉ノードのラベル
```
