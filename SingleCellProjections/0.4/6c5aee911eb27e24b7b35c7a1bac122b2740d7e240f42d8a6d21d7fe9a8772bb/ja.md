```
local_outlier_factor_projection(data::DataMatrix, full::DataMatrix, base::DataMatrix, base_full::DataMatrix; k=10, col="LOF_projection", matrix=:keep, var=:copy)
```

`local_outlier_factor_projection!`のドキュメントを参照してください。このバージョンは`data`をインプレースで変更しません。

また、[`local_outlier_factor_projection!`](@ref)、[`local_outlier_factor_projection_table`](@ref)、[`local_outlier_factor`](@ref)も参照してください。
