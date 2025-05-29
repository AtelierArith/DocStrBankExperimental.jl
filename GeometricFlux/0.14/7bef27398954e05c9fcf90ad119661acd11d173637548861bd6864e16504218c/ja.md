```
EEquivGraphConv(in_dim=>out_dim, pos_dim, edge_dim; init=glorot_uniform)
```

E(n)-等変グラフニューラルネットワーク層。

# 引数

  * `in_dim::Int`: ノード特徴次元。データは[特徴; 座標]の形式であると仮定されるため、`in_dim`は入力ベクトルの次元よりも厳密に小さくなければなりません。
  * `out_dim`: 層の出力は次元`out_dim` + (入力ベクトルの次元 - `in_dim`)になります。
  * `hidden_dim::Int`: 位置エンコーディングの次元。
  * `edge_dim::Int`: エッジ特徴の次元。
  * `init`: ニューラルネットワークの初期化関数。

# 例

```jldoctest
julia> in_dim, out_dim, pos_dim = 3, 5, 2
(3, 5, 2)

julia> egnn = EEquivGraphConv(in_dim=>out_dim, pos_dim, in_dim)
EEquivGraphConv(ϕ_edge=Chain(Dense(10 => 2), Dense(2 => 2)), ϕ_x=Chain(Dense(2 => 2), Dense(2 => 1; bias=false)), ϕ_h=Chain(Dense(5 => 2), Dense(2 => 5)))
```

静的グラフでの層のトレーニングについては[`WithGraph`](@ref)を、位置エンコーディングについては[`EEquivGraphPE`](@ref)を参照してください。
