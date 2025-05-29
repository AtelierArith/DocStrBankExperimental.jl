```
solve_frame(values::Vector{Float64}, p::FrameOptParams; linsolve_alg = UMFPACKFactorization())
```

Solve and store all relevant intermediate variables after an analysis step. This function is the basis of ALL subsequent structural analysis
