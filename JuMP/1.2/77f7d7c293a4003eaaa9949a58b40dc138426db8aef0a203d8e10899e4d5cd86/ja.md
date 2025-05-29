```
value(v::VariableRef; result = 1)
```

変数 `v` の値を、ソルバーによって最近返された結果のインデックス `result` に関連付けて返します。

値を要求する前に、結果が存在するかどうかを確認するには [`has_values`](@ref) を使用してください。

また、[`result_count`](@ref) も参照してください。
