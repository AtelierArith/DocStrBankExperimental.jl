```
objective_function(stochasticprogram::StochasticProgram,
                   T::Type{<:AbstractJuMPScalar}=objective_function_type(model))
```

`stochasticprogram`の完全な目的関数を表す型`T`のオブジェクトを返します。目的が型`T`に変換できない場合はエラーになります。
