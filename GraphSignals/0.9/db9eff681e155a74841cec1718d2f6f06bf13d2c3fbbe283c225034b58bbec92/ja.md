```
kneighbors_graph(X, k, metric; include_self=false, weighted=false)
kneighbors_graph(X, k; include_self=false, weighted=false)
```

ノードの特徴から `k`-最近傍近隣 (kNN) グラフを生成します。これは `FeaturedGraph` オブジェクトを返し、kNN グラフとノード特徴 `X` を含みます。

# 引数

  * `X::AbstractMatrix`: 各ノードの特徴行列で、サイズは `(feat_dim, num_nodes)` です。
  * `k`: kNN グラフにおける各ノードの最近傍の数。
  * `metric::Metric`: 任意の2つのノード間の距離を測定するための距離メトリック。

Distances からの距離オブジェクトを受け入れます。

  * `include_self::Bool`: ノード自身との距離を最近傍に含めるかどうか。
  * `weighted::Bool`: kNN グラフにおけるエッジの重みとして距離を使用できるかどうか。

# 使用法

```jldoctest
julia> using GraphSignals, Distances

julia> nf = rand(Float32, 10, 1024);

julia> fg = kneighbors_graph(nf, 5)
FeaturedGraph:
	Directed graph with (#V=1024, #E=5120) in adjacency matrix
	Node feature:	ℝ^10 <Matrix{Float32}>

julia> fg = kneighbors_graph(nf, 5, Cityblock())
FeaturedGraph:
    Directed graph with (#V=1024, #E=5120) in adjacency matrix
    Node feature:	ℝ^10 <Matrix{Float32}>

julia> nf = rand(Float32[0, 1], 10, 1024);

julia> fg = kneighbors_graph(nf, 5, Jaccard(); include_self=true)
FeaturedGraph:
    Directed graph with (#V=1024, #E=5120) in adjacency matrix
    Node feature:	ℝ^10 <Matrix{Float32}>
```
