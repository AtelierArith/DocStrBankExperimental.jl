```
npa_moment(operators)
```

オペレーター（単項式または多項式）のベクトルが与えられたときに、NPAモーメント行列を構築します。返されるモーメント行列は、モーメント行列の実部の表現であり、すなわち、モーメント行列とその複素共役を足して2で割ったものです。これは、単項式としてスパース行列の形で多項式の形で返されます。

# 例

```julia-repl
julia> gamma = npa_moment([Id, A1, A2, B1, B2]);

julia> gamma[A1]
5×5 SparseArrays.SparseMatrixCSC{Float64, Int64} with 2 stored entries:
  ⋅   1.0   ⋅    ⋅    ⋅
 1.0   ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅

julia> QuantumNPA.repack(gamma)
5×5 Matrix{Polynomial}:
 Id  A1     A2     B1     B2
 A1  Id     A1 A2  A1 B1  A1 B2
 A2  A1 A2  Id     A2 B1  A2 B2
 B1  A1 B1  A2 B1  Id     B1 B2
 B2  A1 B2  A2 B2  B1 B2  Id
```

```julia-repl
julia> gamma = npa_moment([Id, A1 + A2, A1 - A2]);

julia> gamma[A1]
3×3 SparseArrays.SparseMatrixCSC{Float64, Int64} with 4 stored entries:
  ⋅   1.0  1.0
 1.0   ⋅    ⋅
 1.0   ⋅    ⋅


julia> gamma[A2]
3×3 SparseArrays.SparseMatrixCSC{Float64, Int64} with 4 stored entries:
   ⋅   1.0  -1.0
  1.0   ⋅     ⋅
 -1.0   ⋅     ⋅

julia> QuantumNPA.repack(gamma)
3×3 Matrix{Polynomial}:
 Id       A1 + A2             A1 - A2
 A1 + A2  2.0 Id + 2.0 A1 A2  0
 A1 - A2  0                   2.0 Id - 2.0 A1 A2
```
