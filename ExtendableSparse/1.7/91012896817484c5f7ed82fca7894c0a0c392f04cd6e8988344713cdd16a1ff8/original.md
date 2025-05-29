```
    LinearSolvePreconBuilder(; method=UMFPACKFactorization())
```

Return callable object constructing a formal left preconditioner from a sparse LU factorization using LinearSolve as the `precs` parameter for a  [`BlockPreconBuilder`](@ref)  or  iterative methods wrapped by LinearSolve.jl.
