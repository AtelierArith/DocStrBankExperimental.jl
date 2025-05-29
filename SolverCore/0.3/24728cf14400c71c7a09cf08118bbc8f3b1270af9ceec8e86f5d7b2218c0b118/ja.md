```
set_multipliers!(stats::GenericExecutionStats{T, S, V}, y::S, zL::V, zU::V)
```

`y`、`zL`、および `zU` を `stats` に関連付けられた一般的な制約、下限制約、および上限制約に対する最適な乗数として登録し、それらを信頼できるものとしてマークします。
