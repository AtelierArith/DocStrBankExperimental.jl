```
Lookups
```

Module for [`Lookup`](@ref)s and [`Selector`](@ref)s used in DimensionalData.jl

`Lookup` defines traits and `AbstractArray` wrappers that give specific behaviours for a lookup index when indexed with [`Selector`](@ref).

For example, these allow tracking over array order so fast indexing works even when  the array is reversed.

To load `Lookup` types and methods into scope:

```julia
using DimensionalData
using DimensionalData.Lookups
```
