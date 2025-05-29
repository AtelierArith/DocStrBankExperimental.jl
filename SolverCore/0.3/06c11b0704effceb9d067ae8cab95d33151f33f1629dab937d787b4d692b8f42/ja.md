```
set_bounds_multipliers!(stats::GenericExecutionStats{T, S, V}, zL::V, zU::V)
```

`zL` と `zU` をそれぞれ下限制約および上限制約に関連付けられた最適乗数として `stats` に登録し、それらを信頼できるものとしてマークします。
