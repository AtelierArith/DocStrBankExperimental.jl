```
    SimplexLP(P::LP{T}; settings=Settings{T}(), min=true, Phase1=false)
    SimplexLP(c, A, b, d, u; settings=Settings{T}(), min=true, Phase1=false)
```

solve LP by simplex method. If `min=false`, we maximize the objective function

Outputs     x               : solution,  N x 1 vector     S               : Vector{Status}, (N+J)x1     status          : 1 unique; 0 infeasible; 2 infinitely many sol; 3 unbounded

See also [`Status`](@ref), [`LP`](@ref), [`Settings`](@ref), [`cDantzigLP`](@ref), [`maxImprvLP`](@ref)
