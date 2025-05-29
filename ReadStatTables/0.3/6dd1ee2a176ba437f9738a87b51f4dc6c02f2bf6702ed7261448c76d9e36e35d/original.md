```
ReadStatTable{Cols} <: Tables.AbstractColumns
```

A `Tables.jl`-compatible column table that collects data read from or written to a Stata, SAS or SPSS file processed with the `ReadStat` C library. File-level and variable-level metadata can be retrieved and modified via methods compatible with `DataAPI.jl`. For a `ReadStatTable` constructed by [`readstat`](@ref), `Cols` is either `ReadStatColumns` or `ChainedReadStatColumns` depending on whether multiple threads are used for parsing the data file. For a `ReadStatTable` constructed for [`writestat`](@ref), `Cols` is allowed to be a column table type for any `Tables.jl`-compatible table. See also [`ReadStatMeta`](@ref) and [`ReadStatColMeta`](@ref) for the included metadata.
