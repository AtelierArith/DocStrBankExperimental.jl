```
remove_all_but!(solver::GenericSolver, path::Vector{Int}, new_domain::BitVector)
```

Reduce the domain of the hole located at the `path`, to the `new_domain`. It is assumed the path points to a hole, otherwise an exception will be thrown. It is assumed new_domain ⊆ domain. For example: [1, 0, 1, 0] ⊆ [1, 0, 1, 1]
