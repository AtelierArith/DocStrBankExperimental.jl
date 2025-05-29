CDCost

Representation of a [`DAG`](@ref)'s cost as estimated by the [`GlobalMetricEstimator`](@ref).

# Fields:

`.data`: The total data transfer.
`.compute_effort`: The total compute effort.
`.compute_intensity`: The compute intensity, will always equal `.compute_effort / .data`.

!!! note
    Note that the `compute_intensity` doesn't necessarily make sense in the context of only operation costs. It will still work as intended when adding/subtracting to/from a `graph_cost` estimate.

