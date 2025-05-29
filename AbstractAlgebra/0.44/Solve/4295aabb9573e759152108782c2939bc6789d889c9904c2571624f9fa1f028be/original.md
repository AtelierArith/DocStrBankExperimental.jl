```
can_solve_with_solution_and_kernel(A::MatElem{T}, b::Vector{T}; side::Symbol = :left) where T
can_solve_with_solution_and_kernel(A::MatElem{T}, b::MatElem{T}; side::Symbol = :left) where T
can_solve_with_solution_and_kernel(C::SolveCtx{T}, b::Vector{T}; side::Symbol = :left) where T
can_solve_with_solution_and_kernel(C::SolveCtx{T}, b::MatElem{T}; side::Symbol = :left) where T
```

Return `true`, $x$ of same type as $b$ solving the linear system $xA = b$, together with a matrix $K$ giving the kernel of $A$ (i.e. $KA = 0$), if such a solution exists. Return `false`, an empty vector or matrix and an empty matrix, if the system has no solution.

If `side == :right`, the system $Ax = b$ is solved.

If a context object `C` is supplied, then the above applies for `A = matrix(C)`.

See also [`solve`](@ref solve(::Union{MatElem{T}, SolveCtx{T}}, ::Union{Vector{T}, MatElem{T}}) where T) and [`kernel`](@ref kernel(::Union{MatElem, SolveCtx})).
