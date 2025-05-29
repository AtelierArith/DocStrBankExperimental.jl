```
itr = nodes(node)
```

ノードデータではなく、ノードを返すイテレータ `itr` を作成します。

# 例

```julia
julia> foreach(unfold!, nodes(root))
```

は、ツリー内の各ノードが展開されることを保証します。
