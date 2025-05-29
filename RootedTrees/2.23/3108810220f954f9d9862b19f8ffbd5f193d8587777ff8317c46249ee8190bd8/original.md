```
PartitionIterator(t::AbstractRootedTree)
```

Iterator over all partition forests and skeletons of the rooted tree `t`. This is basically a pure iterator version of [`all_partitions`](@ref). In particular, the partition forest may only be realized as an iterator. Similar to [`RootedTreeIterator`](@ref), you should `copy` the iterates if you want to store or modify them during the iteration since they may be views to internal caches.

See also [`partition_forest`](@ref), [`partition_skeleton`](@ref), and [`PartitionForestIterator`](@ref).

# References

Section 2.3 of

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
