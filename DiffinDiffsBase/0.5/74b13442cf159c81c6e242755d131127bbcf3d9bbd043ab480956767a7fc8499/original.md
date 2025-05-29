```
GroupSample <: StatsStep
```

Call [`DiffinDiffsBase.groupsample`](@ref) to obtain one of the instances of `esample` that have been grouped by equality (`hash`) for allowing later comparisons based on object-id.

This step is only useful when working with [`@specset`](@ref) and [`proceed`](@ref).
