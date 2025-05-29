```
DirectSolve <: SmoothAlgorithm
```

Solve the ridge regressions with alternative smoothing parameters by directly repeating each penalized least squares problem.

This algorithm is intended to generate the most accurate estimates for each smoothing parameter when the computational cost is not a concern. For a faster alternative, see [`DemmlerReinsch`](@ref).
