```julia
sortDFG(vars; by, kwargs...)

```

Convenience wrapper for `Base.sort`. Sort variable (factor) lists in a meaningful way (by `timestamp`, `label`, etc), for example `[:april;:x1_3;:x1_6;]` Defaults to sorting by timestamp for variables and factors and using `natural_lt` for Symbols. See Base.sort for more detail.

Notes

  * Not fool proof, but does better than native sort.

Example

`sortDFG(ls(dfg))` `sortDFG(ls(dfg), by=getLabel, lt=natural_lt)`

Related

ls, lsf
