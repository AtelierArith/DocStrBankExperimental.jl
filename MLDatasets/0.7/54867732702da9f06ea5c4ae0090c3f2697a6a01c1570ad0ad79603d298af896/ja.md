```
ChickenPox(; normalize= true, num_timesteps_in = 8 , num_timesteps_out = 8, dir = nothing)
```

ChickenPoxデータセットは、2004年から2014年の間にハンガリーでの郡レベルの水痘の症例を含んでいます。

`ChickenPox`は、ノードが郡を表し、エッジが近隣を表すグラフで構成されており、ノードインデックスと郡名の対応を含むメタデータ辞書があります。

ノードの特徴は、各郡における週ごとの水痘の症例数です。これは、サイズが `(1, num_nodes, num_timesteps_in)` の配列の配列として表されます。ターゲット値は、各郡における週ごとの水痘の症例数です。これは、サイズが `(1, num_nodes, num_timesteps_out)` の配列の配列として表されます。いずれの場合も、2つの連続した配列は1タイムステップずつシフトされています。

データセットは、[Pytorch Geometric Temporalリポジトリ](https://pytorch-geometric-temporal.readthedocs.io/en/latest/modules/dataset.html#torch_geometric_temporal.dataset.chickenpox.ChickenpoxDatasetLoader)から取得され、データセットに関する詳細は論文["Chickenpox Cases in Hungary: a Benchmark Dataset for Spatiotemporal Signal Processing with Graph Neural Networks"](https://arxiv.org/pdf/2102.08100)に記載されています。

# キーワード引数

  * `normalize::Bool`: Zスコア正規化を使用してデータを正規化するかどうか。デフォルトは `true`。
  * `num_timesteps_in::Int`: 入力特徴のためのタイムステップの数、ここでは週の数。デフォルトは `8`。
  * `num_timesteps_out::Int`: ターゲット値のためのタイムステップの数、ここでは週の数。デフォルトは `8`。
  * `dir::String`: データセットを保存するディレクトリ。デフォルトは `nothing`。

# 例

```julia-repl
julia> using JSON3 # import JSON3

julia> dataset = ChickenPox()
dataset ChickenPox:
  metadata  =>    Dict{Symbol, Any} with 20 entries
  graphs    =>    1-element Vector{MLDatasets.Graph}

julia> dataset.graphs[1].num_nodes # 20郡
20

julia> size(dataset.graphs[1].node_data.features[1]) 
(1, 20, 8)

julia> dataset.metadata[:BUDAPEST] # ノード5はブダペスト郡に対応
5
```
