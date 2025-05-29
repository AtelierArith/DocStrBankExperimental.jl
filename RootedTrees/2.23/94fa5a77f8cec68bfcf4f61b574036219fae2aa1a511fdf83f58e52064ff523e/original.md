```
all_partitions(t::RootedTree)
```

Create all partition forests and skeletons of a rooted tree `t`. This returns vectors of the return values of [`partition_forest`](@ref) and [`partition_skeleton`](@ref) when looping over all possible edge sets.

See also [`PartitionIterator`](@ref).

# References

Section 2.3 of

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
