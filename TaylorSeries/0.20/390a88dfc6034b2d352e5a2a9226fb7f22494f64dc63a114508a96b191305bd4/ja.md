```
get_variables(T::Type, [order::Int=get_order()])
```

`TaylorN{T}` ベクトルを返し、各エントリは独立変数を表します。`set_variables` が変更されていない場合、デフォルトの `_params_TaylorN_` 値を使用しますが、`order` は内部の `num_vars` や `variable_names` の値を変更せずにユーザーによって明示的に設定できます。`T` を省略すると、デフォルトで `Float64` になります。
