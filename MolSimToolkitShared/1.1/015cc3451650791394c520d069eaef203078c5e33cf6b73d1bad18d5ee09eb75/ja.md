```
wrap_to_first(x, unit_cell_matrix)
```

点 `x` の座標をラップして、返される座標がすべて正の座標を持つ最初の単位セル内に収まるようにします。単位セルはサイズ `(N,N)` の行列である必要があります。

## 例

```jldoctest
julia> using MolSimToolkitShared: wrap_to_first

julia> uc = [10.0 0.0 0.0; 0.0 10.0 0.0; 0.0 0.0 10.0]
3×3 Matrix{Float64}:
 10.0   0.0   0.0
  0.0  10.0   0.0
  0.0   0.0  10.0

julia> wrap_to_first([15.0, 13.0, 2.0], uc)
3-element Vector{Float64}:
 5.0
 3.0000000000000004
 2.0
```
