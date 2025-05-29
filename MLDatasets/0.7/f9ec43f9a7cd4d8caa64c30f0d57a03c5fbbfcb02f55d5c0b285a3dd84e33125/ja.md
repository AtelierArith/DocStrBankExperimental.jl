```
AQSOL(; split=:train, dir=nothing)
```

論文 [Graph Neural Network for Predicting Aqueous Solubility of Organic Molecules](http://arxiv.org/abs/2003.00982) からの AQSOL (Aqueous Solubility) データセット。

このデータセットには、小さな有機分子を表す 9,882 のグラフが含まれています。各グラフは分子を表し、ノードは原子に対応し、エッジは結合に対応します。ノードの特徴は原子番号を表し、エッジの特徴は結合の種類を表します。ターゲットは、mol/L で測定された分子の水溶性です。

# 引数

  * `split`: 読み込むデータセットの分割。`:train`、`:val`、または `:test` のいずれかです。デフォルトは `:train` です。
  * `dir`: データセットがあるディレクトリ。

# 例

```julia-repl
julia> using MLDatasets

julia> data = AQSOL()
dataset AQSOL:
  split     =>    :train
  metadata  =>    Dict{String, Any} with 1 entry
  graphs    =>    7985-element Vector{MLDatasets.Graph}

julia> length(data)
7985

julia> g = data[1]
Graph:
  num_nodes   =>    23
  num_edges   =>    42
  edge_index  =>    ("42-element Vector{Int64}", "42-element Vector{Int64}")
  node_data   =>    (features = "23-element Vector{Int64}",)
  edge_data   =>    (features = "42-element Vector{Int64}",)

julia> g.num_nodes
23

julia> g.node_data.features
23-element Vector{Int64}:
 0
 1
 1
 ⋮
 1
 1
 1

julia> g.edge_index
([2, 3, 3, 4, 4, 5, 5, 6, 6, 7  …  18, 19, 19, 20, 20, 21, 20, 22, 20, 23], [3, 2, 4, 3, 5, 4, 6, 5, 7, 6  …  19, 18, 20, 19, 21, 20, 22, 20, 23, 20])
```
