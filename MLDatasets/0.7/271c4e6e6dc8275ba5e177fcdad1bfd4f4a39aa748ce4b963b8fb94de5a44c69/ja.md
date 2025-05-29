```
WindMillEnergy(; size, normalize=true, num_timesteps_in=8, num_timesteps_out=8, dir=nothing)
```

WindMillEnergyデータセットは、2年以上にわたるヨーロッパの国の風車の時間ごとのエネルギー出力のコレクションを含んでいます。

`WindMillEnergy`は、ノードが風車を表すグラフです。エッジの重みは、風車間の関係の強さを表します。ノードの数は固定されており、データセットのサイズに依存します。`small`の場合は11、`medium`の場合は26、`large`の場合は319です。

ノードの特徴とターゲットは、風車の時間ごとのエネルギー出力の数です。これは、サイズが`(1, num_nodes, num_timesteps_in)`の配列の配列として表されます。いずれの場合も、2つの連続した配列は1時間のステップでシフトされます。

# キーワード引数

  * `size::String`: データセットのサイズで、`small`、`medium`、または`large`のいずれかです。
  * `normalize::Bool`: Zスコア正規化を使用してデータを正規化するかどうか。デフォルトは`true`です。
  * `num_timesteps_in::Int`: 入力特徴のための時間ステップの数、ここでは時間の数です。デフォルトは`8`です。
  * `num_timesteps_out::Int`: ターゲット値のための時間ステップの数、ここでは時間の数です。デフォルトは`8`です。
  * `dir::String`: データセットを保存するディレクトリ。デフォルトは`nothing`です。

# 例

```julia-repl
julia> using JSON3

julia> dataset = WindMillEnergy(;size= "small");

julia> dataset.graphs[1]
Graph:
  num_nodes   =>    11
  num_edges   =>    121
  edge_index  =>    ("121-element Vector{Int64}", "121-element Vector{Int64}")
  node_data   =>    (features = "17456-element Vector{Any}", targets = "17456-element Vector{Any}")
  edge_data   =>    121-element Vector{Float32}

julia> size(dataset.graphs[1].node_data.features[1])
(1, 11, 8)
```
