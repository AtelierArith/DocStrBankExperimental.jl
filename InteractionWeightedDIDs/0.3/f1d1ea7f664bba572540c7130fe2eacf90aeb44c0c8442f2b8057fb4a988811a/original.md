```
GroupFEterms <: StatsStep
```

Call [`InteractionWeightedDIDs.groupfeterms`](@ref) to obtain one of the instances of `feterms` that have been grouped by equality (`hash`) for allowing later comparisons based on object-id.

This step is only useful when working with [`@specset`](@ref) and [`proceed`](@ref).
