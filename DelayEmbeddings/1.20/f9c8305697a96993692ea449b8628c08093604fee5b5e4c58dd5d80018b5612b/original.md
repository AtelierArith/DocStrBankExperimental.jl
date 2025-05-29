```
neighborhood(point, tree, ntype)
neighborhood(point, tree, ntype, n::Int, w::Int = 1)
```

Return a vector of indices which are the neighborhood of `point` in some `data`, where the `tree` was created using `tree = KDTree(data [, metric])`. The `ntype` is the type of neighborhood and can be any subtype of [`AbstractNeighborhood`](@ref).

Use the second method when the `point` belongs in the data, i.e. `point = data[n]`. Then `w` stands for the Theiler window (positive integer). Only points that have index `abs(i - n) ≥ w` are returned as a neighborhood, to exclude close temporal neighbors. The default `w=1` is the case of excluding the `point` itself.

## References

`neighborhood` simply interfaces the functions `NearestNeighbors.knn` and `inrange` from [NearestNeighbors.jl](https://github.com/KristofferC/NearestNeighbors.jl) by using the argument `ntype`.
