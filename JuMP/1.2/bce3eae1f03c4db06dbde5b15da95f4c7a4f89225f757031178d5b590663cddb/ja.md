```
set_string_names_on_creation(model::Model, value::Bool)
```

`@variable`(@ref) および `@constraint`(@ref) マクロの `set_string_name` キーワードのデフォルト引数を `value` に設定します。これは、`model` 内のすべての変数と制約に `String` 名を割り当てるかどうかを決定するために使用されます。

デフォルトでは、`value` は `true` です。ただし、大きなモデルの場合、`set_string_names_on_creation(model, false)` を呼び出すことで、印刷やソルバーログメッセージの可読性を低下させる代わりにパフォーマンスを向上させることができます。
