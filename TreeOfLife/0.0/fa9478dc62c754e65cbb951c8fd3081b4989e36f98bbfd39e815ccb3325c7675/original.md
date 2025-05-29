```
getages(tree::ChronoTree; average=mean_, reltol=1e-6) :: Vector{Float64}
```

Return ages (from the root node) of all nodes of the tree.

The argument `average` defines the method for summarizing the ages to one; by  default it is set to `mean_`.

The argument `reltol` is a tolerance of relative error. By default it is set  to `1e-6`. To suppress the judgment, set `reltol=NaN`.
