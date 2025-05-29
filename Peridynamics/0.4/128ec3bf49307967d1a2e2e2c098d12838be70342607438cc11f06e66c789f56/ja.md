```
uniform_box(lx, ly, lz, ΔX0; kwargs...)
```

長さ `lx`、`ly`、`lz` の直方体内に均等に分布した点のグリッドを作成し、点の間隔は `ΔX0` です。

# 引数

  * `lx::Real`: x次元の長さ。
  * `ly::Real`: y次元の長さ。
  * `lz::Real`: z次元の長さ。
  * `ΔX0::Real`: 点の間隔。

# キーワード

  * `center`: 直方体の中心の座標。デフォルト: `(0, 0, 0)`

# 戻り値

  * `position::Matrix{Float64}`: 点の位置を持つ `3×n_points` 行列。
  * `volume::Vector{Float64}`: 各点の体積を持つベクトル。

# 例

```julia-repl
julia> position, volume = uniform_box(10, 10, 10, 2);

julia> position
3×125 Matrix{Float64}:
 -4.0  -2.0   0.0   2.0   4.0  -4.0  -2.0  …  0.0  2.0  4.0  -4.0  -2.0  0.0  2.0  4.0
 -4.0  -4.0  -4.0  -4.0  -4.0  -2.0  -2.0     2.0  2.0  2.0   4.0   4.0  4.0  4.0  4.0
 -4.0  -4.0  -4.0  -4.0  -4.0  -4.0  -4.0     4.0  4.0  4.0   4.0   4.0  4.0  4.0  4.0

julia> volume
125-element Vector{Int64}:
 8
 8
 8
 8
 ⋮
 8
 8
 8
 8
```
