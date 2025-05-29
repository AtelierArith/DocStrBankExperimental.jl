```
SplittingIterator(t::RootedTree)
```

Iterator over all splitting forests and subtrees of the rooted tree `t`. This is basically an iterator version of [`all_splittings`](@ref).

See also [`partition_forest`](@ref) and [`partition_skeleton`](@ref).

# References

Section 2.2 of

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
