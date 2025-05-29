```
dof_tstat(r::LocalProjectionResult)
```

推定結果からt統計量を計算するために使用される自由度を返します。これは、分散共分散推定量に応じて[`dof_residual`](@ref)とは異なる場合があります。
