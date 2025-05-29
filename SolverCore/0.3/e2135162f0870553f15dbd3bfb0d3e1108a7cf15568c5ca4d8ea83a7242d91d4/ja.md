```
set_primal_residual!(stats::GenericExecutionStats{T, S, V}, primal::T)
```

`primal`を`stats`に最適なプライマル残差として登録し、信頼できるものとしてマークします。
