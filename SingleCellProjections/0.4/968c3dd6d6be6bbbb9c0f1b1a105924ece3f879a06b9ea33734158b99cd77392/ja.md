```
local_outlier_factor_projection_table(data::DataMatrix, full::DataMatrix, base::DataMatrix, base_full::DataMatrix; k=10, col="LOF_projection", matrix=:keep, var=:copy)
```

`local_outlier_factor_projection!` のドキュメントを参照してください。これは、観測IDとプロジェクションのLOF値を含む列 `col` を持つDataFrameを返します。

また、[`local_outlier_factor_projection!`](@ref)、[`local_outlier_factor_projection`](@ref)、[`local_outlier_factor_table`](@ref) も参照してください。
