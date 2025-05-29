```
set_residuals!(stats::GenericExecutionStats{T, S, V}, primal::T, dual::T)
```

`primal` と `dual` をそれぞれ `stats` に最適なプライマルおよびデュアルの実行可能性残差として登録し、それらを信頼できるものとしてマークします。
