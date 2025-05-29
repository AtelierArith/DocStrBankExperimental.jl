```
npa2sdp(expr, level; eq=[], ge=[])
```

指定されたNPA階層のレベルで、与えられた量子最適化問題のNPA緩和を生成します。

これは基本的に`npa_moment`関数を使用してモーメント行列を生成し、その後、モーメント行列を第二引数として再度`npa2sdp`を呼び出します。これにより、問題の実部を取得し、代入によって等式制約を排除します。

# 例

```julia-repl
julia> S = A1*(B1 + B2) + A2*(B1 - B2)
A1 B1 + A1 B2 + A2 B1 - A2 B2

julia> (objective, moments) = npa2sdp(S, 1, eq=[A2*B1 - Id]);

julia> objective
Id + A1 B1 + A1 B2 - A2 B2

julia> moments[1][Id]
5×5 SparseArrays.SparseMatrixCSC{Float64, Int64} with 7 stored entries:
 1.0   ⋅    ⋅    ⋅    ⋅
  ⋅   1.0   ⋅    ⋅    ⋅
  ⋅    ⋅   1.0  1.0   ⋅
  ⋅    ⋅   1.0  1.0   ⋅
  ⋅    ⋅    ⋅    ⋅   1.0

julia> QuantumNPA.repack(moments[1])
5×5 Matrix{Polynomial}:
 Id  A1     A2     B1     B2
 A1  Id     A1 A2  A1 B1  A1 B2
 A2  A1 A2  Id     Id     A2 B2
 B1  A1 B1  Id     Id     B1 B2
 B2  A1 B2  A2 B2  B1 B2  Id
```
