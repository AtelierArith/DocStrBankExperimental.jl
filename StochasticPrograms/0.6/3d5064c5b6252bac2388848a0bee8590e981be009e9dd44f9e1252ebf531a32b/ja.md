```
num_constraints(stochasticprogram::StochasticProgram{N}, stage::Integer, function_type, set_type)::Int64
```

`stochasticprogram`の`stage`に現在ある意思決定制約の数を返します。この関数の型は`function_type`であり、セットの型は`set_type`です。通常の制約がクエリされた場合はエラーになります。その場合、関連する変数に[`@decision`](@ref)を注釈付けするか、最初に関連するJuMPサブ問題をクエリし、通常の`all_constraints`関数を使用してください。
