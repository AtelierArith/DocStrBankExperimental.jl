```
solvealgebraicequations(V::AbstractAlgebraicSet, algo::AbstractAlgebraicSolver)::Union{Nothing, Vector{<:Vector}}}
```

Solve the algebraic equations for which `V` is the set of solutions using the algorithm `algo`. Returns a nullable which is `null` if `V` is not zero-dimensional and is the list of solutions otherwise.
