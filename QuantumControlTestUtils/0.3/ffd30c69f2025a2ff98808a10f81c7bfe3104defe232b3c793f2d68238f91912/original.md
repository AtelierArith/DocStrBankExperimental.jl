Print out a coverage summary from existing coverage data.

```julia
show_coverage(paths=["./src", "./ext"]; root=pwd(), sort_by=nothing)
```

prints a a table showing the tracked files in `paths`, the total number of tracked lines in that file ("Total"), the number of lines with coverage ("Hit"), the number of lines without coverage ("Missed") and the "Coverage" as a percentage.

The coverage data is collected from `.cov` files in `paths` as well as `tracefile-*.info` files in `root`.

Optionally, the table can be sorted by passing the name of a column to `sort_by`, e..g. `sort_py=:Missed`.
