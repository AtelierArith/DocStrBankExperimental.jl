```
すべての制約(stochasticprogram::StochasticProgram, stage::Integer, function_type, set_type)::Vector{<:SPConstraintRef}
```

`stochasticprogram`の`stage`に現在存在するすべての意思決定制約のリストを返します。関数のタイプは`function_type`で、セットのタイプは`set_type`です。制約は作成時間順に並べられます。通常の制約がクエリされた場合はエラーになります。その場合、関連する変数に[`@decision`](@ref)を注釈付けするか、最初に関連するJuMPサブ問題をクエリし、通常の`all_constraints`関数を使用してください。
