```
swap_node(expr::AbstractRuleNode, new_expr::AbstractRuleNode, path::Vector{Int})
```

`expr`内のノードを、`path`で指定された位置に`new_expr`で置き換えます。パスは、ルートノードから始まる子インデックスのシーケンスです。
