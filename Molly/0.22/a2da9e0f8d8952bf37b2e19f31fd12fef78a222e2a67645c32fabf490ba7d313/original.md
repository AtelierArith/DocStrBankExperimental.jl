```
use_neighbors(inter)
```

Whether a pairwise interaction uses the neighbor list, default `false`.

Custom pairwise interactions can define a method for this function. For built-in interactions such as [`LennardJones`](@ref) this function accesses the `use_neighbors` field of the struct.
