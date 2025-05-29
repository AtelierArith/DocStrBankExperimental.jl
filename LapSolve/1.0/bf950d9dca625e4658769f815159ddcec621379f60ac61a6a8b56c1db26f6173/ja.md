solve*stiff*lap(cost_matrix) -> assignment in cartesian coords

# 例

```julia
julia> using LapSolve

julia> M=rand([1,2,Inf],5,5)
5×5 Array{Float64,2}:
 Inf    Inf      1.0    1.0    1.0
 Inf    Inf    Inf    Inf    Inf
   2.0    1.0  Inf      1.0    2.0
 Inf      2.0    1.0    2.0  Inf
   2.0    2.0    2.0  Inf      1.0

julia> solve_stiff_lap(M)
6-element Array{Tuple{Int64,Int64},1}:
 (1, 4)        ← 行 1 は列 4 に割り当てられています
 (2, -1)       ← 割り当てがないため -1、行 2 は何にも割り当てられていません
 (3, 2)
 (4, 3)
 (5, 5)
 (-1, 1)       ← 列 1 は何にも割り当てられていません
```
