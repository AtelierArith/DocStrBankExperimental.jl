Site{T}

絶対座標を持つサイトを表します。

座標には :x, :y, :z でアクセスできます。

# 例

```julia-repl
julia> site = Site(Float64[1,2,3], 1, :H)
Site{Vector{Float64}}:
    H    1    1.00000    2.00000    3.00000

julia> site.x
1.0

julia> cell=Cell(Lattice(10, 10, 10), [:H], [[1.,2., 3.]])
Cell with 1 ions
Lattice: 
  10.000      0.000      0.000
   0.000     10.000      0.000
   0.000      0.000     10.000
Sites: 
   H     1.00000     2.00000     3.00000
```

`Site` オブジェクトの位置を更新すると、`Cell` オブジェクトの位置も更新されます。

```julia-repl
julia> site = cell[1]
Site{SubArray{Float64, 1, Matrix{Float64}, Tuple{Base.Slice{Base.OneTo{Int64}}, Int64}, true}}:
    H    1    1.00000    2.00000    3.00000

julia> site.position[1] 
1.0

julia> site.position[1] = 2.;

3×1 Matrix{Float64}:
 2.0
 2.0
 3.0
```
