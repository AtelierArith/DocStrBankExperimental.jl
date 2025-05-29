```
add_rule!(g::AbstractGrammar, e::Expr)
```

文法にルールを追加します。

### 使用法:

```
    add_rule!(grammar, :("Real = Real + Real"))
```

構文は[`@csgrammar`](@ref)および[`@cfgrammar`](@ref)の構文と同じですが、単一のルールのみがサポートされています。

!!! warning
    すでに文法にルールがある場合、この関数への呼び出しは無視されます。

