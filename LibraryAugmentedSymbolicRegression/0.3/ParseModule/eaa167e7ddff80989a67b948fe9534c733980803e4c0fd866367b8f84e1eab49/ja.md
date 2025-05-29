```
parse_expr(expr_str::String, options) -> AbstractExpressionNode
```

文字列（例：`string_tree`から）とオプションオブジェクト（演算子、変数命名規則などを含む）を与えると、AbstractExpressionNodeを再構築します。
