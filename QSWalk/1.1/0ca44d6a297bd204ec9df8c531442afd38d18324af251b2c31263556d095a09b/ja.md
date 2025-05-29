```
proj(vector)
```

ベクトル `vector` によって張られた部分空間への射影を返します。

# 例

```jldoctest; setup = :(using QSWalk)
julia> v = 1/sqrt(2) * (ket(1, 3)+ket(3, 3))
3-element SparseArrays.SparseVector{Float64,Int64} with 2 stored entries:
  [1]  =  0.707107
  [3]  =  0.707107

julia> proj(v)
3×3 SparseArrays.SparseMatrixCSC{Float64,Int64} with 4 stored entries:
  [1, 1]  =  0.5
  [3, 1]  =  0.5
  [1, 3]  =  0.5
  [3, 3]  =  0.5
```
