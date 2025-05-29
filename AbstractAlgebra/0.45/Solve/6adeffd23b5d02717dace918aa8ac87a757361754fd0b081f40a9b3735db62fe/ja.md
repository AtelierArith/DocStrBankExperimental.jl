```
can_solve_with_solution(A::MatElem{T}, b::Vector{T}; side::Symbol = :left) where T
can_solve_with_solution(A::MatElem{T}, b::MatElem{T}; side::Symbol = :left) where T
can_solve_with_solution(C::SolveCtx{T}, b::Vector{T}; side::Symbol = :left) where T
can_solve_with_solution(C::SolveCtx{T}, b::MatElem{T}; side::Symbol = :left) where T
```

線形システム $xA = b$ を解く解が存在する場合、`true` と $b$ と同じ型の $x$ を返します。解が存在しない場合は、`false` と空のベクトルまたは行列を返します。

`side == :right` の場合、システム $Ax = b$ が解かれます。

コンテキストオブジェクト `C` が提供されると、上記は `A = matrix(C)` に対して適用されます。

詳細は [`solve`](@ref solve(::Union{MatElem{T}, SolveCtx{T}}, ::Union{Vector{T}, MatElem{T}}) where T) を参照してください。
