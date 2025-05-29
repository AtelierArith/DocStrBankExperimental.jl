```
solve_for_update(F::LUFactor, newcol::SparseVector{Float64, Int64}; getsol::Bool=false) -> SparseVector{Float64, Int64}
```

Solve forward system in preparation to update the factorization. `newcol` holds the column to be inserted into the factorized matrix in the next call to [`update`](@ref). When `getsol = true`, then the solution from the forward solve with right-hand side `newcol` is returned. Otherwise only the update is prepared.
