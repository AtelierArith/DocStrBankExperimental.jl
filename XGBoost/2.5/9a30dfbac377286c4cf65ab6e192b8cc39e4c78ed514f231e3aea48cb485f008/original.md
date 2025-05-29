```
importancereport(b::Booster)
```

Show a convenient text display of the table output by [`importancetable`](@ref).

This is intended entirely for display purposes, see [`importance`](@ref) for how to retrieve feature importance statistics directly.

!!! note
    In Julia >= 1.9, you have to load Term.jl to be able to use this functionality.

