```
maxmin(atoms::AbstractVector{<:Atom}; selection)
```

原子ベクトルの最大および最小座標、および各方向の長さ（最大から最小を引いた値）を返します。

### 例

```julia-repl
julia> protein = wget("1LBD");

julia> maxmin(protein)
 
 最小原子座標: xmin = [-29.301, 57.178, 45.668]
 最大原子座標: xmax = [47.147, 99.383, 86.886]
 各方向の長さ: xlength = [76.448, 42.205, 41.217999999999996]

```
