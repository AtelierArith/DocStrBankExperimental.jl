```
solve_for_update(F::LUFactor, pos::Int64; getsol::Bool=false) -> SparseVector{Float64, Int64}
```

Solve transposed system in preparation to update the factorization. `pos` holds the column index of the factorized matrix to be replaced in the next call to [`update`](@ref). When `getsol = true`, then the solution from the transposed solve with a unit vector as right-hand side is returned. Otherwise only the update is prepared.
