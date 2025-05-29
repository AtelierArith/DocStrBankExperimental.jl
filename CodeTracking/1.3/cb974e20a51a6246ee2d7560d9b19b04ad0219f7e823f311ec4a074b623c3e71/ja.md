```
code_expr(f, types)
```

指定された型の `f` のメソッド定義の式を返します。

Revise がロードされていない場合、`nothing` を返すことがあります。そのような場合、`Meta.parse(code_string(f, types))` を呼び出すことが代替手段となることがあります。
