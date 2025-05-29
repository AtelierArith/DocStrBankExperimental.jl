```
(cell1, cell2, cell3, i) :: Site
```

Four indices identifying a single site in a [`System`](@ref). The first three indices select the unit cell and the last index selects the sublattice, i.e., the $i$th atom within the unit cell.

This object can be used to index `dipoles` and `coherents` fields of a `System`. A `Site` is also required to specify inhomogeneous interactions via functions such as [`set_field_at!`](@ref) or [`set_exchange_at!`](@ref).

Note that the definition of a cell may change when a system is reshaped. In this case, it is convenient to construct the `Site` using [`position_to_site`](@ref), which always takes a position in fractional coordinates of the original lattice vectors.
