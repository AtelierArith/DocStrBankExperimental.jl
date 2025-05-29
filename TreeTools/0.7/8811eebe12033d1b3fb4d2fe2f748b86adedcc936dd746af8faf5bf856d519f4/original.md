```
write_newick(io::IO, tree::Tree; kwargs...)
write_newick(filename::AbstractString, tree::Tree, mode="w"; kwargs...)
write_newick(tree::Tree; kwargs...)
```

Write Newick string corresponding to `tree` to `io` or `filename`. If output is not provided, return the Newick string. If `internal_labels == false`, do not write labels of internal nodes in the string.
