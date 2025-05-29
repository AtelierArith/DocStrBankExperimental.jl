```
Axis(axis::AbstractString) <: QueryOperation
```

A query operation for specifying a result axis. In a string [`Query`](@ref), this is specified using the `/` operator followed by the axis name.

This needs to be specified at least once for a vector query (e.g., `/ cell : batch`), and twice for a matrix (e.g., `/ cell / gene : UMIs`). Axes can be filtered using Boolean masks using [`And`](@ref), [`AndNot`](@ref), [`Or`](@ref), [`OrNot`](@ref), [`Xor`](@ref) and [`XorNot`](@ref) (e.g., `/ gene & is_marker : is_noisy`). Alternatively, a single entry can be selected from the axis using [`IsEqual`](@ref) (e.g., `/ gene = FOX1 : is_noisy`, `/ cell / gene = FOX1 : UMIs`, `/ cell = C1 / gene = FOX1 : UMIs`). Finally, a matrix can be reduced into a vector, and a vector to a scalar, using [`ReductionOperation`](@ref) (e.g., `/ gene / cell : UMIs %> Sum %> Mean`).

!!! note
    This, [`Names`](@ref) and [`Lookup`](@ref) are the only [`QueryOperation`](@ref)s that also works as a complete [`Query`](@ref).

