```
QuasiDiagonal(A::AbstractQuasiMatrix)
```

`A`の対角成分から行列を構築します。

# 例

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Array{Int64,2}:
 1  2  3
 4  5  6
 7  8  9

julia> QuasiDiagonal(A)
3×3 QuasiDiagonal{Int64,Array{Int64,1}}:
 1  ⋅  ⋅
 ⋅  5  ⋅
 ⋅  ⋅  9
```
