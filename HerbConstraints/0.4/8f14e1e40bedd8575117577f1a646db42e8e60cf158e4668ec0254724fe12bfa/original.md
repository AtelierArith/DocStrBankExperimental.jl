```
remove!(solver::GenericSolver, path::Vector{Int}, rules::Vector{Int})
```

Remove all `rules` from the domain of the hole located at the `path`. It is assumed the path points to a hole, otherwise an exception will be thrown.
