```
local_outlier_factor_projection_table(data::DataMatrix, full::DataMatrix, base::DataMatrix, base_full::DataMatrix; k=10, col="LOF_projection", matrix=:keep, var=:copy)
```

See `local_outlier_factor_projection!` for documentation. This returns a DataFrame with observation IDs and a column `col` with LOF values for the projection.

See also: [`local_outlier_factor_projection!`](@ref), [`local_outlier_factor_projection`](@ref), [`local_outlier_factor_table`](@ref)
