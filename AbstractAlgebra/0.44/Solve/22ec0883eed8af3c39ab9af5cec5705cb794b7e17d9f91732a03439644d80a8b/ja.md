```
solve(A::MatElem{T}, b::Vector{T}; side::Symbol = :left) where T
solve(A::MatElem{T}, b::MatElem{T}; side::Symbol = :left) where T
solve(C::SolveCtx{T}, b::Vector{T}; side::Symbol = :left) where T
solve(C::SolveCtx{T}, b::MatElem{T}; side::Symbol = :left) where T
```

$$
A
$$

に対して線形システム$xA = b$を解くと、$b$と同じ型の$x$を返します。`side == :left`（デフォルト）の場合、または$Ax = b$の場合は`side == :right`です。

解が存在しない場合、エラーが発生します。

コンテキストオブジェクト`C`が提供されると、上記は$A = matrix(C)$に適用されます。

[`can_solve_with_solution`](@ref can_solve_with_solution(::Union{MatElem{T}, SolveCtx{T}}, ::Union{Vector{T}, MatElem{T}}) where T)も参照してください。

# 例

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
