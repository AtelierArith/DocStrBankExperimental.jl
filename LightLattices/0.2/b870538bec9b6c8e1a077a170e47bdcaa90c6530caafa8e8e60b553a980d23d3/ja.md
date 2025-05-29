```julia
struct RegularLattice{D, T, PB, CT, L<:Union{Nothing, Symbol}} <: LightLattices.AbstractLattice{D, T, PB}
```

  * `lattice_dims::NTuple{D, Int64} where D`: 各基準方向に沿った基底セルの数。
  * `basis::StaticArraysCore.SMatrix{D, D} where D`: 基本格子の基底ベクトルの座標。`basis[:, i]`は$i$-th基底ベクトルを返します。
  * `unit_cell::Any`: 格子の単位セル。
  * `label::Union{Nothing, Symbol}`: 格子のラベル。
  * `num_of_cells::Int64`: セルの総数。
  * `num_of_nodes::Int64`: ノードの総数。
  * `central_cell::CartesianIndex`: 中央セルの直交インデックス（次元の長さが偶数の場合は近似です）。

この型は、境界条件`PB`を持つ`D`次元空間におけるノードの規則的な配置を記述します（周期的境界条件の場合は`PB=true`、自由周期的境界条件の場合は`PB=false`）。一般的な格子は、同一のセル（ノードの組み合わせ）から構成され、ブラヴェ格子として配置されています。
