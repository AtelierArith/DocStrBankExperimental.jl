```
local_outlier_factor_table(data::DataMatrix, full::DataMatrix; k=10, col="LOF")
```

See `local_outlier_factor!` for documentation. This returns a DataFrame with observation IDs and a column `col` with LOF values.

See also: [`local_outlier_factor!`](@ref), [`local_outlier_factor`](@ref), [`local_outlier_factor_projection_table`](@ref)
