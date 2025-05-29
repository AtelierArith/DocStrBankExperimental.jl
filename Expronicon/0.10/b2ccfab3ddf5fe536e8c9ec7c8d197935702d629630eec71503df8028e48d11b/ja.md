```
@test_expr <expr> == <expr>
```

2つの式が意味的に同等であるかをテストします。これは `compare_expr` を使用して、式が同等であるかを判断し、`Expr(:curly, ...)` や `Expr(:where, ...)` で生成された `Symbol` のようなものを無視します。

!!! note
    このマクロは、`Test` モジュール名をインポートするために `using Test` を1回必要とします。

