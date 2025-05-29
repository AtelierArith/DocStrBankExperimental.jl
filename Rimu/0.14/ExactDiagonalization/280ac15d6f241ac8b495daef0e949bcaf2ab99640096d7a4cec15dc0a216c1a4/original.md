```
init(p::ExactDiagonalizationProblem, [algorithm]; kwargs...)
```

Initialize a solver for an [`ExactDiagonalizationProblem`](@ref) `p` with an optional `algorithm`. Returns a solver instance that can be solved with [`solve`](@ref solve(::ExactDiagonalizationProblem)).

For a description of the keyword arguments, see the documentation for [`ExactDiagonalizationProblem`](@ref).
