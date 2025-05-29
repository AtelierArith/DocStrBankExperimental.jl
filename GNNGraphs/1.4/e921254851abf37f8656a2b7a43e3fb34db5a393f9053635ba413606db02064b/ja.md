```
GNNHeteroGraph(data; [ndata, edata, gdata, num_nodes])
GNNHeteroGraph(pairs...; [ndata, edata, gdata, num_nodes])
```

異種グラフ構造を表す型です。これは[`GNNGraph`](@ref)に似ていますが、ノードとエッジは異なるタイプです。

# コンストラクタ引数

  * `data`: `(source_type, edge_type, target_type)`の三つ組を`(source, target)`インデックスベクトル（またはエッジの重みが存在する場合は`(source, target, weight)`）にマッピングする辞書または反復可能なオブジェクト。
  * `pairs`: 複数の関係をペアとして渡すことは、`data=Dict(pairs...)`を渡すことと同等です。
  * `ndata`: ノードの特徴。配列の辞書または配列の名前付きタプル。各配列の最後の次元のサイズは`g.num_nodes`によって指定されなければなりません。
  * `edata`: エッジの特徴。配列の辞書または配列の名前付きタプル。デフォルトは`nothing`。各配列の最後の次元のサイズは`g.num_edges`によって指定されなければなりません。デフォルトは`nothing`。
  * `gdata`: グラフの特徴。最後の次元のサイズが`num_graphs`である配列または配列の名前付きタプル。デフォルトは`nothing`。
  * `num_nodes`: 各タイプのノードの数。指定されていない場合は、`data`から推測されます。デフォルトは`nothing`。

# フィールド

  * `graph`: `(source_type, edge_type, target_type)`の三つ組を`(source, target)`インデックスベクトルにマッピングする辞書。
  * `num_nodes`: 各タイプのノードの数。
  * `num_edges`: 各タイプのエッジの数。
  * `ndata`: ノードの特徴。
  * `edata`: エッジの特徴。
  * `gdata`: グラフの特徴。
  * `ntypes`: ノードのタイプ。
  * `etypes`: エッジのタイプ。

# 例

```julia
julia> using GNNGraphs

julia> nA, nB = 10, 20;

julia> num_nodes = Dict(:A => nA, :B => nB);

julia> edges1 = (rand(1:nA, 20), rand(1:nB, 20))
([4, 8, 6, 3, 4, 7, 2, 7, 3, 2, 3, 4, 9, 4, 2, 9, 10, 1, 3, 9], [6, 4, 20, 8, 16, 7, 12, 16, 5, 4, 6, 20, 11, 19, 17, 9, 12, 2, 18, 12])

julia> edges2 = (rand(1:nB, 30), rand(1:nA, 30))
([17, 5, 2, 4, 5, 3, 8, 7, 9, 7  …  19, 8, 20, 7, 16, 2, 9, 15, 8, 13], [1, 1, 3, 1, 1, 3, 2, 7, 4, 4  …  7, 10, 6, 3, 4, 9, 1, 5, 8, 5])

julia> data = ((:A, :rel1, :B) => edges1, (:B, :rel2, :A) => edges2);

julia> hg = GNNHeteroGraph(data; num_nodes)
GNNHeteroGraph:
  num_nodes: (:A => 10, :B => 20)
  num_edges: ((:A, :rel1, :B) => 20, (:B, :rel2, :A) => 30)

julia> hg.num_edges
Dict{Tuple{Symbol, Symbol, Symbol}, Int64} with 2 entries:
(:A, :rel1, :B) => 20
(:B, :rel2, :A) => 30

# ノードの特徴を追加しましょう
julia> ndata = Dict(:A => (x = rand(2, nA), y = rand(3, num_nodes[:A])),
                    :B => rand(10, nB));

julia> hg = GNNHeteroGraph(data; num_nodes, ndata)
GNNHeteroGraph:
    num_nodes: (:A => 10, :B => 20)
    num_edges: ((:A, :rel1, :B) => 20, (:B, :rel2, :A) => 30)
    ndata:
    :A  =>  (x = 2×10 Matrix{Float64}, y = 3×10 Matrix{Float64})
    :B  =>  x = 10×20 Matrix{Float64}

# タイプ:Aのノードの特徴にアクセス
julia> hg.ndata[:A].x
2×10 Matrix{Float64}:
    0.825882  0.0797502  0.245813  0.142281  0.231253  0.685025  0.821457  0.888838  0.571347   0.53165
    0.631286  0.316292   0.705325  0.239211  0.533007  0.249233  0.473736  0.595475  0.0623298  0.159307
```

同様に、同種グラフ型については[`GNNGraph`](@ref)を、ランダム異種グラフを生成する関数については[`rand_heterograph`](@ref)を参照してください。
