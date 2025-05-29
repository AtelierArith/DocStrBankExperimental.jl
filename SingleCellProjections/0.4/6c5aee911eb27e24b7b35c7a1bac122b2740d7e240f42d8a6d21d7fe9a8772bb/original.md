```
local_outlier_factor_projection(data::DataMatrix, full::DataMatrix, base::DataMatrix, base_full::DataMatrix; k=10, col="LOF_projection", matrix=:keep, var=:copy)
```

See `local_outlier_factor_projection!` for documentation. This version does not modify `data` in place.

See also: [`local_outlier_factor_projection!`](@ref), [`local_outlier_factor_projection_table`](@ref), [`local_outlier_factor`](@ref)
