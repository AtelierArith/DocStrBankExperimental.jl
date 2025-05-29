FCIアルゴリズムの出力を保持するための有向非巡回グラフ構造体

### 可変構造体

```julia
DAG(
* `name::AbstractString` : DAGオブジェクトの名前
* `g::Graphs.SimpleGraphs.SimpleDiGraph{Int64}` : CausalInference.DiGraph
* `g_tuple_list::Vector{Tuple{Int, Int}}` : エッジのベクトルとしてのDAG定義、例: [(:a, :b), ...]
* `g_dot_str::AbstractString` : DAGのdot表現（例: GraphVizで使用）
* `vars::Vector{Symbol}` : 初期DAGの変数
* `est_g::Graphs.SimpleGraphs.SimpleDiGraph{Int64}` : CausalInference.DiGraph
* `est_g_tuple_list::Vector{Tuple{Int, Int}}` : エッジのベクトルとしてのDAG定義、例: [(:a, :b), ...]
* `est_g_dot_str::AbstractString` : DAGのdot表現（例: GraphVizで使用）
* `df::DataFrame` : 変数の観測
* `cov::NamedArray` : NamedArrayとしての共分散行列
)
```

APIの一部、エクスポートされています。
