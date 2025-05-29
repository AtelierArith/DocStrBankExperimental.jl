`SPerm{T}(m::AbstractMatrix)`  If  `m`  is  a  signed  permutation  matrix, returns  the corresponding signed permutation of  type `T`. If omitted, `T` is taken to be `Int16`.

```julia-repl
julia> m=[0 -1 0;-1 0 0;0 0 -1]
3×3 Matrix{Int64}:
  0  -1   0
 -1   0   0
  0   0  -1

julia> SPerm(m)
(1,-2)(3,-3)
```
