```
@call_marginalrule NodeType(:edge) (argument1 = value1, argument2 = value2, ..., [ meta = ... ])
```

`@call_marginalrule` マクロは、より簡単な構文で `marginalrule` メソッドを呼び出すのに役立ちます。マクロの構造は `@marginalrule` マクロとほぼ同じですが、`begin ... end` ブロックはなく、代わりに各引数には `=` 演算子で指定された値が必要です。

参照: [`@marginalrule`](@ref), [`marginalrule`](@ref), [`@call_rule`](@ref)
