```
uniform_sphere(diameter, ΔX0; kwargs...)
```

特定の `diameter` を持つ球体内に均等に分布した点のグリッドを作成します。点の間隔 `ΔX0` により、球の表面にエッジが発生することがあります。

# 引数

  * `diameter::Real`: 球の直径。
  * `ΔX0::Real`: 点の間隔。

# キーワード

  * `center`: 球の中心の座標。デフォルト: `(0, 0, 0)`

# 戻り値

  * `position::Matrix{Float64}`: 点の位置を持つ `3×n_points` 行列。
  * `volume::Vector{Float64}`: 各点の体積を持つベクトル。

# 例

```julia-repl
julia> position, volume = uniform_sphere(10, 2);

julia> position
3×81 Matrix{Float64}:
 -2.0   0.0   2.0  -2.0   0.0   2.0  -2.0  …   0.0   2.0  -2.0  0.0  2.0  -2.0  0.0  2.0
 -2.0  -2.0  -2.0   0.0   0.0   0.0   2.0     -2.0  -2.0   0.0  0.0  0.0   2.0  2.0  2.0
 -4.0  -4.0  -4.0  -4.0  -4.0  -4.0  -4.0      4.0   4.0   4.0  4.0  4.0   4.0  4.0  4.0

julia> volume
81-element Vector{Int64}:
 8
 8
 8
 8
 8
 ⋮
 8
 8
 8
 8
 8
```
