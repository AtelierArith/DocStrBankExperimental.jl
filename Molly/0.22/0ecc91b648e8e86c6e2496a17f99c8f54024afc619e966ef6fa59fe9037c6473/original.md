```
TreeNeighborFinder(; eligible, dist_cutoff, special, n_steps)
```

Find close atoms by distance using a tree search.

Can not be used if one or more dimensions has infinite boundaries. Can not be used with [`TriclinicBoundary`](@ref).
