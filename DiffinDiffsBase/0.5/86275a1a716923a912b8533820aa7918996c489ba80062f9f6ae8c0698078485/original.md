```
VecColumnTable <: AbstractColumns
```

A `Tables.jl`-compatible column table that stores data as `Vector{AbstractVector}` and column names as `Vector{Symbol}`. Retrieving columns by column names is achieved with a `Dict{Symbol,Int}` that maps names to indices.

This table type is designed for retrieving and iterating dynamically generated columns for which specialization on names and order of columns are not desired. It is not intended to be directly constructed for interactive usage.
