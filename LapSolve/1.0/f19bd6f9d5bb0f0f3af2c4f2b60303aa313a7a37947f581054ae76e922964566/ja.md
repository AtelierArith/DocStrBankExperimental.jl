solve*lap(cost*matrix) -> (assignment, cost)

# 例

```julia
julia> using LapSolve

julia> M=rand(1:100,3,3)
3×3 Array{Int64,2}:
 66  83  92
 17  92  65
 30  84  18

julia> solve_lap(M)
([2, 1, 3], 118)
```
