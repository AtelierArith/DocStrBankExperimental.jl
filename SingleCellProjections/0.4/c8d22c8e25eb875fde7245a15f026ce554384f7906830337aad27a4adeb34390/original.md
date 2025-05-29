```
local_outlier_factor(data::DataMatrix, full::DataMatrix; k=10, col="LOF", matrix=:keep, var=:copy)
```

See `local_outlier_factor!` for documentation. This version does not modify `data` in place.

See also: [`local_outlier_factor!`](@ref), [`local_outlier_factor_table`](@ref), [`local_outlier_factor_projection`](@ref)
