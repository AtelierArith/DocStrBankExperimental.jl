```
super(cell::Cell, factors::AbstractMatrix{<:Integer})
super(cell::Cell, factors::AbstractVector{<:Integer})
super(cell::Cell, factor::Integer)
```

Create a supercell from `cell`.

!!! note
    Currently, only integral replications are supported.

