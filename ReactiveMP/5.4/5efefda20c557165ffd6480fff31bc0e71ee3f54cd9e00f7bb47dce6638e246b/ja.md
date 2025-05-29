```
@call_rule NodeType(:edge, Constraint) (argument1 = value1, argument2 = value2, ..., [ meta = ..., addons = ... ])
```

`@call_rule` マクロは、より簡単な構文で `rule` メソッドを呼び出すのに役立ちます。マクロの構造は `@rule` マクロとほぼ同じですが、`begin ... end` ブロックはなく、代わりに各引数には `=` 演算子で指定された値が必要です。

`@call_rule` は、関数形式の仕様の前にオプションのリストを受け入れます。例えば：

```julia
@call_rule [ return_addons = true ] NodeType(:edge, Constraint) (argument1 = value1, argument2 = value2, ..., [ meta = ..., addons = ... ])
```

利用可能なオプションのリストは次のとおりです：

  * `return_addons` - `@call_rule` に `(result, addons)` のタプルを返すよう強制します
  * `fallback` - 指定された `NodeType` と引数に対してルールが定義されていない場合に使用するフォールバックルールを指定します

参照： [`@rule`](@ref), [`rule`](@ref), [`@call_marginalrule`](@ref)
