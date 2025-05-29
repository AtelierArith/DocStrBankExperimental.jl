```
value(v::GenericVariableRef; result = 1)
```

最も最近ソルバーによって返された結果のインデックス `result` に関連付けられた変数 `v` の値を返します。

値を要求する前に、結果が存在するかどうかを確認するには [`primal_status`](@ref) を使用してください。

また、[`result_count`](@ref) も参照してください。
