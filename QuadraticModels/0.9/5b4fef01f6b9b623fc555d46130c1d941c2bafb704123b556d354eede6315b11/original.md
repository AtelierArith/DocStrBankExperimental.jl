```
sol = postsolve(qm::QuadraticModel{T, S}, psqm::PresolvedQuadraticModel{T, S}, 
                sol_in::QMSolution{S}) where {T, S}
```

Retrieve the solution `sol = (x, y, s_l, s_u)` of the original QP `qm` given the solution of the presolved QP (`psqm`) `sol_in` of type [`QMSolution`](@ref). `sol_in.s_l` and `sol_in.s_u` can be sparse or dense vectors, but the output `sol.s_l` and `sol.s_u` are dense vectors. 
