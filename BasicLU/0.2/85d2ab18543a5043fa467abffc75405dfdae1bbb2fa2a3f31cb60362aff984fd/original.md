```
update(F::LUFactor, pivot::Float64) -> Float64
```

Update the factorization after a column modification. The column position and the new column must have been set in previous calls to [`solve_for_update`](@ref).

`pivot` is the pivot element corresponding to the update operation; i.e. when column `j` of `B` is to be replaced by vector `v`, then `pivot = (B\v)[j]`. The absolute difference between `pivot` and a recomputed version can be obtained with `getinfo(F, :pivotError)`; this is also the return value. A pivot error larger than 1e-8, say, indicates numerical instability and suggests refactorization.

An error is thrown when the recomputed pivot element is below the absolute pivot tolerance. In this case no update is performed and the old factorization remains valid.
