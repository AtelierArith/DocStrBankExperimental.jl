```
And(property::AbstractString) <: QueryOperation
```

A query operation for restricting the set of entries of an [`Axis`](@ref). In a string [`Query`](@ref), this is specified using the `&` operator, followed by the name of an axis property to look up to compute the mask.

The mask may be just the fetched property (e.g., `/ gene & is_marker` will restrict the result vector to only marker genes). If the value of the property is not Boolean, it is automatically compared to `0` or the empty string, depending on its type (e.g., `/ cell & type` will restrict the result vector to only cells which were given a non-empty-string type annotation). It is also possible to fetch properties from other axes, and use an explicit [`ComparisonOperation`](@ref) to compute the Boolean mask (e.g., `/ cell & batch => age > 1` will restrict the result vector to cells whose batch has an age larger than 1).
