```
can_solve_with_solution_and_kernel(A::MatElem{T}, b::Vector{T}; side::Symbol = :left) where T
can_solve_with_solution_and_kernel(A::MatElem{T}, b::MatElem{T}; side::Symbol = :left) where T
can_solve_with_solution_and_kernel(C::SolveCtx{T}, b::Vector{T}; side::Symbol = :left) where T
can_solve_with_solution_and_kernel(C::SolveCtx{T}, b::MatElem{T}; side::Symbol = :left) where T
```

`true`を返し、$x$は$b$と同じ型で線形システム$xA = b$を解き、行列$K$は$A$のカーネルを与えます（すなわち、$KA = 0$）。そのような解が存在する場合、`false`、空のベクトルまたは行列、空の行列を返します。システムに解がない場合。

`side == :right`の場合、システム$Ax = b$が解かれます。

コンテキストオブジェクト`C`が提供されると、上記は`A = matrix(C)`に適用されます。

[`solve`](@ref solve(::Union{MatElem{T}, SolveCtx{T}}, ::Union{Vector{T}, MatElem{T}}) where T)および[`kernel`](@ref kernel(::Union{MatElem, SolveCtx}))も参照してください。
