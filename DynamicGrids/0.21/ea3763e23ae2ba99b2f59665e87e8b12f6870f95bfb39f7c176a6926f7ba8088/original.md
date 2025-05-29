```
NeighborhoodRule <: Rule
```

A Rule that only accesses a neighborhood centered around the current cell. `NeighborhoodRule` is applied with the method:

```julia
applyrule(data::AbstractSimData, rule::MyNeighborhoodRule, state, I::Tuple{Int,Int})
```

`NeighborhoodRule` must have a `neighborhood` method or field, that holds a [`Neighborhood`](@ref) object. `neighbors(rule)` returns an iterator over the surrounding cell pattern defined by the `Neighborhood`.

For each cell in the grids the neighborhood buffer will be updated for use in the `applyrule` method, managed to minimise array reads.

This allows memory optimisations and the use of high-perforance routines on the neighborhood buffer. It also means that and no bounds checking is required in neighborhood code.

For neighborhood rules with multiple read grids, the first is always the one used for the neighborhood, the others are passed in as additional state for the cell. Any grids can be written to, but only for the current cell.
