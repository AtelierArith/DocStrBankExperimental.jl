```
local_outlier_factor!(data::DataMatrix, full::DataMatrix; k=10, col="LOF")
```

Compute the Local Outlier Factor (LOF) for each observation in `data`, and add as column to `data.obs` with the name `col`.

When working with projected `DataMatrices`, use [`local_outlier_factor_projection!`](@ref) instead.

NB: This function might be very slow for high values of `k`.

First, the `k` nearest neighbors are found for each observation in `data`. Then, the Local Outlier Factor is computed by considering the distance between the neighbors, but this time in the `full` DataMatrix. Thus `full` must have the same observations as are present in `data`.

A LOF value smaller than or close to one is means that the observation is an inlier, but a LOF value much larger than one means that the observation is an inlier.

By specifiying `full=data`, this is coincides with the standard definition for Local Outlier Factor. However, it is perhaps more useful to find neighbors in a dimension reduced space (after e.g. `svd` (PCA) or `umap`), but then compute distances in the high dimensional space (typically after normalization). This way, an observation is concidered an outlier if the reduction to a lower dimensional space didn't properly represent the neighborhood of the observation.

!!! note
    The interface is not yet fully decided and subject to change.


# Examples

Compute the Local Outlier Factor, with nearest neighbors based only on `reduced`, but later using distances in `full` for the actual LOF computation.

```julia
julia> reduced = svd(normalized; nsv=10)

julia> local_outlier_factor!(reduced, normalized; k=10)
```

See also: [`local_outlier_factor`](@ref), [`local_outlier_factor_table`](@ref), [`local_outlier_factor_projection!`](@ref)
