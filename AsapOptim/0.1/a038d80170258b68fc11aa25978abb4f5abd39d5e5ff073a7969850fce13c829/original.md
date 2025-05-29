```
solve_truss(values::Vector{Float64}, p::TrussOptParams; linsolve_alg = UMFPACKFactorization())
```

Solve and store all relevant intermediate variables after an analysis step. This function is the basis of ALL subsequent structural analysis
