```
PartitionForestIterator(t::AbstractRootedTree, edge_set)
```

Lazy iterator representation of the [`partition_forest`](@ref) of the rooted tree `t`. Similar to [`RootedTreeIterator`](@ref), you should `copy` the iterates if you want to store or modify them during the iteration since they may be views to internal caches.

See also [`partition_forest`](@ref), [`partition_skeleton`](@ref), and [`PartitionIterator`](@ref).

# References

Section 2.3 of

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
