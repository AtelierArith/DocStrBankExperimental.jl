```
GNNGraph(data; [graph_type, ndata, edata, gdata, num_nodes, graph_indicator, dir])
GNNGraph(g::GNNGraph; [ndata, edata, gdata])
```

ノード、エッジ、およびグラフ自体に関連付けられた特徴配列を格納するグラフ構造を表す型です。

特徴配列は、便利な辞書のようなインターフェースと名前付きタプルのようなインターフェースを提供する[`DataStore`](@ref)オブジェクトとして、フィールド`ndata`、`edata`、および`gdata`に格納されます。特徴は、構築時に渡すことも、後で追加することもできます。

`GNNGraph`は、グラフ内の接続を表すさまざまな`data`オブジェクトから構築できます。内部表現の型は`graph_type`によって決まります。

別の`GNNGraph`から構築されると、内部グラフ表現は保持され、共有されます。ノード/エッジ/グラフの特徴も保持されますが、キーワード引数`ndata`、`edata`、および`gdata`によって明示的に設定されている場合を除きます。

`GNNGraph`は、複数のグラフを一緒にバッチ処理することもできます（[`MLUtils.batch`](@ref)または[`SparseArrays.blockdiag`](@ref）を参照）。フィールド`g.graph_indicator`には、各ノードのグラフメンバーシップが含まれています。

`GNNGraph`は常に有向グラフであり、したがって各エッジはソースノードとターゲットノードによって定義されます（[`edge_index`](@ref）を参照）。自己ループ（ノードが自分自身に接続するエッジ）や複数エッジ（同じノードのペア間のエッジが複数ある場合）もサポートされています。

`GNNGraph`はGraphs.jlの`AbstractGraph`であるため、そのライブラリからのほとんどの機能をサポートしています。

# 引数

  * `data`: グラフトポロジーを表すデータ。可能な型は

      * 隣接行列
      * 隣接リスト
      * ソースおよびターゲットベクトルを含むタプル（COO表現）
      * Graphs.jlのグラフ
  * `graph_type`: GNNGraphで使用される基盤となる表現を指定するキーワード引数。現在サポートされている値は

      * `:coo`。グラフはタプル`(source, target)`として表され、`k`-thエッジはノード`source[k]`をノード`target[k]`に接続します。オプションで、エッジの重みも与えることができます: `(source, target, weights)`。
      * `:sparse`。スパース隣接行列表現。
      * `:dense`。密な隣接行列表現。

    デフォルトは`:coo`で、現在最もサポートされている型です。
  * `dir`: 隣接行列または隣接リスト入力データ`g`が与えられたときの仮定されるエッジの方向。可能な値は`:out`と`:in`。デフォルトは`:out`。
  * `num_nodes`: ノードの数。指定されていない場合、`g`から推測されます。デフォルトは`nothing`。
  * `graph_indicator`: バッチ処理されたグラフの場合、各ノードのグラフ割り当てを含むベクトル。デフォルトは`nothing`。
  * `ndata`: ノードの特徴。最後の次元が`num_nodes`のサイズを持つ配列または配列の名前付きタプル。
  * `edata`: エッジの特徴。最後の次元が`num_edges`のサイズを持つ配列または配列の名前付きタプル。
  * `gdata`: グラフの特徴。最後の次元が`num_graphs`のサイズを持つ配列または配列の名前付きタプル。

# 例

```julia
using GNNGraphs

# 隣接リスト表現から構築
data = [[2,3], [1,4,5], [1], [2,5], [2,4]]
g = GNNGraph(data)

# ノード、エッジ、およびバッチ処理されたグラフの数
g.num_nodes  # 5
g.num_edges  # 10
g.num_graphs # 1

# COO表現での同じグラフ
s = [1,1,2,2,2,3,4,4,5,5]
t = [2,3,1,4,5,3,2,5,2,4]
g = GNNGraph(s, t)

# Graphsのグラフから
g = GNNGraph(erdos_renyi(100, 20))

# 作成時に2つのノード特徴配列を追加
g = GNNGraph(g, ndata = (x=rand(100, g.num_nodes), y=rand(g.num_nodes)))

# グラフ作成後に1つのエッジ特徴配列を追加
g.edata.z = rand(16, g.num_edges)

# デフォルト名`x`と`e`でノード特徴とエッジ特徴を追加
g = GNNGraph(g, ndata = rand(100, g.num_nodes), edata = rand(16, g.num_edges))

g.ndata.x # または単に g.x
g.edata.e # または単に g.e

# エッジのソースノードとターゲットノードを収集します。
# ソースとターゲットは両方とも長さnum_edgesのベクトルです
source, target = edge_index(g)
```

`GNNGraph`は、たとえばFlux.jlの`gpu`関数やMLDataDevices.jlのユーティリティを使用してGPUに送信できます。
