```
mutable struct UniformIterator
```

Inner iterator that enumerates all candidate programs of a uniform tree.

  * `solver`: the uniform solver.
  * `outeriter`: outer iterator that is responsible for producing uniform trees. This field is used to dispatch on the [`derivation_heuristic`](@ref).
  * `unvisited_branches`: for each search-node from the root to the current search-node, a list of unviisted branches.
  * `nsolutions`: number of solutions found so far.
