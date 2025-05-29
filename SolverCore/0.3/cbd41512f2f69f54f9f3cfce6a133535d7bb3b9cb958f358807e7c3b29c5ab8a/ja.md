```
set_dual_residual!(stats::GenericExecutionStats{T, S, V}, dual::T)
```

`dual`を`stats`に最適な双対可行残差として登録し、信頼できるものとしてマークします。
