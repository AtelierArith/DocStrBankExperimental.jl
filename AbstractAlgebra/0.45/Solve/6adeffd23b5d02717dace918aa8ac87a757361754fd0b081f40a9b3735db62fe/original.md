```
can_solve_with_solution(A::MatElem{T}, b::Vector{T}; side::Symbol = :left) where T
can_solve_with_solution(A::MatElem{T}, b::MatElem{T}; side::Symbol = :left) where T
can_solve_with_solution(C::SolveCtx{T}, b::Vector{T}; side::Symbol = :left) where T
can_solve_with_solution(C::SolveCtx{T}, b::MatElem{T}; side::Symbol = :left) where T
```

Return `true` and $x$ of same type as $b$ solving the linear system $xA = b$, if such a solution exists. Return `false` and an empty vector or matrix, if the system has no solution.

If `side == :right`, the system $Ax = b$ is solved.

If a context object `C` is supplied, then the above applies for `A = matrix(C)`.

See also [`solve`](@ref solve(::Union{MatElem{T}, SolveCtx{T}}, ::Union{Vector{T}, MatElem{T}}) where T).
