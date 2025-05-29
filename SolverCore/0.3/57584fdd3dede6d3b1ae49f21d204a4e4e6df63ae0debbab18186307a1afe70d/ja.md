```
set_constraint_multipliers!(stats::GenericExecutionStats{T, S, V}, y::S, zL::V, zU::V)
```

`y`を`stats`内の一般的な制約に関連付けられた最適な乗数として登録し、それらを信頼できるものとしてマークします。
