```
Average(field::AbstractField; dims=:, condition=nothing, mask=0)
```

Return `Reduction` representing a spatial average of `field` over `dims`.

Over regularly-spaced dimensions this is equivalent to a numerical `mean!`.

Over dimensions of variable spacing, `field` is multiplied by the appropriate grid length, area or volume, and divided by the total spatial extent of the interval.

See [`ConditionalOperation`](@ref Oceananigans.AbstractOperations.ConditionalOperation) for information and examples using `condition` and `mask` kwargs.
