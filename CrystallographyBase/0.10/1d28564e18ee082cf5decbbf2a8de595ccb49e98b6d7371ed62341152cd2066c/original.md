```
supercell(cell::Cell, repfactors::AbstractMatrix{<:Integer})
supercell(cell::Cell, repfactors::AbstractVector{<:Integer})
supercell(cell::Cell, repfactor::Integer)
```

Create a supercell from `cell`.

!!! note
    Currently, only integral replications are supported.

