```
partition_skeleton(t::AbstractRootedTree, edge_set)
```

Form the partition skeleton of the rooted tree `t`, i.e., the rooted tree obtained by contracting each tree of the partition forest to a single vertex and re-establishing the edges removed to obtain the partition forest.

See also [`partition_forest`](@ref) and [`PartitionIterator`](@ref).

# References

Section 2.3 (and Section 6.1 for colored trees) of

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
