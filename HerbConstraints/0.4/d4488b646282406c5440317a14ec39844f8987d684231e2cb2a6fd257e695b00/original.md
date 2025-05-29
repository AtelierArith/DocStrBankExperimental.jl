```
remove_all_but!(solver::GenericSolver, path::Vector{Int}, rule_index::Int)
```

Fill in the hole located at the `path` with rule `rule_index`. It is assumed the path points to a hole, otherwise an exception will be thrown. It is assumed rule_index ∈ hole.domain.

!!! warning: If the `hole` is known to be in the current tree, the hole can be passed directly.     The caller has to make sure that the hole instance is actually present at the provided `path`.
