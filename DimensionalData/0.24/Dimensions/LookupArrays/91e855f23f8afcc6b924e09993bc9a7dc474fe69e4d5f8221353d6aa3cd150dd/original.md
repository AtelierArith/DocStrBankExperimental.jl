```
LookupArrays
```

Module for [`LookupArrays`](@ref) and [`Selector`]s used in DimensionalData.jl

`LookupArrays` defines traits and `AbstractArray` wrappers that give specific behaviours for a lookup index when indexed with [`Selector`](@ref).

For example, these allow tracking over array order so fast indexing works evne when  the array is reversed.

To load LookupArrays types and methods into scope:

```julia
using DimensionalData
using DimensionalData.LookupArrays
```
