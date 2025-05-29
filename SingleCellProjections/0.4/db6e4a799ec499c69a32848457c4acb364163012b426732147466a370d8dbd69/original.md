```
local_outlier_factor_projection!(data::DataMatrix, full::DataMatrix, base::DataMatrix, base_full::DataMatrix; k=10, col="LOF_projection")
```

Compute the Local Outlier Factor (LOF) for each observation in `data`, and add as column to `data.obs` with the name `col`.

Use `local_outlier_factor_projection!` if you are working with projected data, and [`local_outlier_factor!`](@ref) otherwise.

Parameters:

  * `data` - A `DataMatrix` for which we compute LOF for each observation. Expected to be a `DataMatrix` projected onto `base`, so that the `data` and `base` use the same coordinate system.
  * `full` - A `DataMatrix` with the same observations as `data`, used to compute distances in the LOF computation. Expected to be a `DataMatrix` projected onto `base_full`, so that the `full` and `base_full` use the same coordinate system.
  * `base` - The base `DataMatrix`.
  * `base_full` - The base `DataMatrix`.
  * `k` - The number of nearest neighbors to use. NB: This function might be very slow for high values of `k`.

First, for each observation in `data`, the `k` nearest neighbors in `base` are found. Then, the distance to each neighbor is computed using `full` and `base_full`. Thus `full` must have the same observations as are present in `data`, and `base_full` must have the same observations as `base`.

A LOF value smaller than or close to one is means that the observation is an inlier, but a LOF value much larger than one means that the observation is an inlier.

By specifiying `full=data` and `base_full=base`, this is coincides with the standard definition for Local Outlier Factor. However, it is perhaps more useful to find neighbors in a dimension reduced space (after e.g. `svd` (PCA) or `umap`), but then compute distances in the high dimensional space (typically after normalization). This way, an observation is concidered an outlier if the reduction to a lower dimensional space didn't properly represent the neighborhood of the observation.

!!! note
    The interface is not yet fully decided and subject to change.


# Examples

Compute the Local Outlier Factor (LOF) for each observation in a data set `reduced`, which has been projected onto `base_reduced`.

The nearest neighbors are computed between observations in `reduced` and `base_reduced`, but the distances in the actual LOF computation are between the same observations in `normalized` and `base_normalized`.

```julia
julia> base_reduced = svd(base_normalized; nsv=10)

julia> normalized = project(counts, base_normalized);

julia> reduced = project(normalized, base_reduced);

julia> local_outlier_factor!(reduced, normalized, base_reduced, base_normalized; k=10)
```

See also: [`local_outlier_factor_projection`](@ref), [`local_outlier_factor_projection_table`](@ref), [`local_outlier_factor!`](@ref)
