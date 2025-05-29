```
can_solve(A::MatElem{T}, b::Vector{T}; side::Symbol = :left) where T
can_solve(A::MatElem{T}, b::MatElem{T}; side::Symbol = :left) where T
can_solve(C::SolveCtx{T}, b::Vector{T}; side::Symbol = :left) where T
can_solve(C::SolveCtx{T}, b::MatElem{T}; side::Symbol = :left) where T
```

`side == :left`（デフォルト）または `side == :right` の場合に、線形システム $xA = b$ または $Ax = b$ が解を持つ場合は `true` を返し、そうでない場合は `false` を返します。

コンテキストオブジェクト `C` が提供される場合、上記は `A = matrix(C)` に対して適用されます。

詳細は [`can_solve_with_solution`](@ref can_solve_with_solution(::Union{MatElem{T}, SolveCtx{T}}, ::Union{Vector{T}, MatElem{T}}) where T) を参照してください。

# 例

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
