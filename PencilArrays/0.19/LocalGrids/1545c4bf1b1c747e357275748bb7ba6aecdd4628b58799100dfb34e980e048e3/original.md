```
localgrid((xs, ys, ...), perm = NoPermutation()) -> LocalRectilinearGrid
```

Create a [`LocalRectilinearGrid`](@ref) from a set of orthogonal coordinates `(xs, ys, ...)`, where each element is an `AbstractVector`.

Optionally, one can pass a static permutation (as in `Permutation(2, 1, 3)`) to change the order in which the coordinates are iterated.
