## `hausdorff_metric`

```julia
hausdorff_metric(
    prediction::AbstractArray, ground_truth::AbstractArray;
    per::Union{Nothing, Real}=nothing, directed::Bool=false
)
```

Compute the Hausdorff distance between two masks, `prediction` and `ground_truth`.

This function has multiple methods depending on the arguments provided:

1. Without `per`: Computes the standard Hausdorff distance.
2. With `per`: Computes the Hausdorff distance at the specified percentile.

#### Arguments

  * `prediction`: Predicted mask, 2D or 3D array of `::Bool` or `::Int`.
  * `ground_truth`: Ground truth mask, 2D or 3D array of `::Bool` or `::Int`.
  * `per`: Percentile for the Hausdorff distance (optional).
  * `directed`: If `true`, computes one-sided Hausdorff. Default is `false`.

#### Returns

  * Hausdorff distance or Hausdorff distance at the specified percentile.
