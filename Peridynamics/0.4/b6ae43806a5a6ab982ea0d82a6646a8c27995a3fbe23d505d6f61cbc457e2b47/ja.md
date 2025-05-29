```
uniform_cylinder(diameter::Real, height::Real, ΔX0::Real; kwargs...)
```

特定の `height` を持つ円柱形状に均等に分布した点のグリッドを作成します。`diameter` と点の間隔 `ΔX0` があります。均等な点間隔のため、円柱の表面にエッジが発生する可能性があります。

# 引数

  * `diameter::Real`: 円柱の直径。
  * `height::Real`: 円柱の高さ。
  * `ΔX0::Real`: 点の間隔。

# キーワード

  * `center`: 円柱の中心の座標。デフォルト: `(0, 0, 0)`

# 戻り値

  * `position::Matrix{Float64}`: 点の位置を持つ `3×n_points` 行列。
  * `volume::Vector{Float64}`: 各点の体積を持つベクトル。

# 例

```julia-repl
julia> position, volume = uniform_cylinder(5, 10, 2);

julia> position
3×20 Matrix{Float64}:
 -1.0   1.0  -1.0   1.0  -1.0   1.0  -1.0  …   1.0  -1.0  1.0  -1.0   1.0  -1.0  1.0
 -1.0  -1.0   1.0   1.0  -1.0  -1.0   1.0     -1.0   1.0  1.0  -1.0  -1.0   1.0  1.0
 -4.0  -4.0  -4.0  -4.0  -2.0  -2.0  -2.0      2.0   2.0  2.0   4.0   4.0   4.0  4.0

julia> volume
20-element Vector{Int64}:
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
