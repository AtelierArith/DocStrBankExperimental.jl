```
solve(A::MatElem{T}, b::Vector{T}; side::Symbol = :left) where T
solve(A::MatElem{T}, b::MatElem{T}; side::Symbol = :left) where T
solve(C::SolveCtx{T}, b::Vector{T}; side::Symbol = :left) where T
solve(C::SolveCtx{T}, b::MatElem{T}; side::Symbol = :left) where T
```

Return $x$ of same type as $b$ solving the linear system $xA = b$, if `side == :left` (default), or $Ax = b$, if `side == :right`.

If no solution exists, an error is raised.

If a context object `C` is supplied, then the above applies for `A = matrix(C)`.

See also [`can_solve_with_solution`](@ref can_solve_with_solution(::Union{MatElem{T}, SolveCtx{T}}, ::Union{Vector{T}, MatElem{T}}) where T).

# Example

```jldoctest
julia> A = QQ[2 0 0;0 3 0;0 0 5]
[2//1   0//1   0//1]
[0//1   3//1   0//1]
[0//1   0//1   5//1]

julia> solve(A, one(A))
[1//2   0//1   0//1]
[0//1   1//3   0//1]
[0//1   0//1   1//5]
```
