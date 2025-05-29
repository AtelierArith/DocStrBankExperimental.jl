```
partition_forest(t::RootedTree, edge_set)
```

Form the partition forest of the rooted tree `t` where edges marked with `false` in the `edge_set` are removed. The ith value in the Boolean iterable `edge_set` corresponds to the edge connecting node `i+1` in the level sequence to its parent.

See also [`partition_skeleton`](@ref), [`PartitionIterator`](@ref), and [`PartitionForestIterator`](@ref).

# References

Section 2.3 of

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
