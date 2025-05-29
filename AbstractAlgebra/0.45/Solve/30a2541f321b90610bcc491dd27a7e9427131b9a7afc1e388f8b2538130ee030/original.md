```
can_solve(A::MatElem{T}, b::Vector{T}; side::Symbol = :left) where T
can_solve(A::MatElem{T}, b::MatElem{T}; side::Symbol = :left) where T
can_solve(C::SolveCtx{T}, b::Vector{T}; side::Symbol = :left) where T
can_solve(C::SolveCtx{T}, b::MatElem{T}; side::Symbol = :left) where T
```

Return `true` if the linear system $xA = b$ or $Ax = b$ with `side == :left` (default) or `side == :right`, respectively, has a solution and `false` otherwise.

If a context object `C` is supplied, then the above applies for `A = matrix(C)`.

See also [`can_solve_with_solution`](@ref can_solve_with_solution(::Union{MatElem{T}, SolveCtx{T}}, ::Union{Vector{T}, MatElem{T}}) where T).

# Example

```jldoctest
julia> A = QQ[2 0 0;0 3 0;0 0 5]
[2//1   0//1   0//1]
[0//1   3//1   0//1]
[0//1   0//1   5//1]

julia> can_solve(A,one(A))
true

julia> A = ZZ[2 0 0;0 3 0;0 0 5]
[2   0   0]
[0   3   0]
[0   0   5]

julia> can_solve(A,one(A))
false
```
