汎用のmultiroute_flow関数は、3種類の結果を出力します：

  * ルートの数が0または指定されていない場合、マルチルートフローのブレイキングポイントのセットが返されます。
  * 入力がブレイキングポイントのセットとルート値kに制限されている場合、kルートフローの値のみが返されます。
  * それ以外の場合、1) 最大フローと2) フローマトリックスを含むタプルが返されます。max-flowサブルーチンがBoykov-Kolmogorovアルゴリズムである場合、関連するミンカットが3番目の出力として返されます。

入力がネットワークの場合、次の引数が必要です：

  * flow_graph::ADiGraph                   # 入力グラフ
  * source::Int                           # ソース頂点
  * target::Int                           # ターゲット頂点
  * capacity_matrix::AbstractMatrix{T}  # エッジフロー容量（T<:Real）
  * flow_algorithm::AbstractFlowAlgorithm # フローアルゴリズムのキーワード引数
  * mrf_algorithm::AbstractFlowAlgorithm  # マルチルートフローアルゴリズムのキーワード引数
  * routes::R<:Real                       # ルートの数のキーワード引数

入力がブレイキングポイントのセットとルートの数のみの場合、次の引数が必要です：

  * breakingpoints::Vector{Tuple{T, T, Int}},    # ブレイキングポイントのベクター
  * routes::R<:Real,                             # ルートの数

入力がブレイキングポイントのセット、ルートの数、およびネットワーク記述子の場合、次の引数が必要です：

  * breakingpoints::Vector{Tuple{T1, T1, Int}} # ブレイキングポイントのベクター（T1<:Real）
  * routes::R<:Real                            # ルートの数
  * flow_graph::ADiGraph                        # 入力グラフ
  * source::Int                                # ソース頂点
  * target::Int                                # ターゲット頂点
  * capacity_matrix::AbstractMatrix{T2}      # オプションのエッジフロー容量（T2<:Real）
  * flow_algorithm::AbstractFlowAlgorithm      # アルゴリズムのキーワード引数

関数はデフォルトでPush-relabel（古典的フロー）およびKishimoto（マルチルート）アルゴリズムを使用します。代わりに、使用するアルゴリズムもキーワード引数を通じて指定できます。容量マトリックスが提供されていない場合、各リンクのデフォルト容量は1と見なされます。

mrf_algorithmキーワードは、次の場合にExtended Multiroute Flowに強制されます：

  * ルートの数が非整数
  * ルートの数が0または指定されていない

### 使用例：

（flow*algorithmおよびcapacity*matrixに関するオプションについては、max*flowセクションを参照してください）

```julia

# フローグラフと容量マトリックスを作成
flow_graph = DiGraph(8)
flow_edges = [
    (1, 2, 10), (1, 3, 5),  (1, 4, 15), (2, 3, 4),  (2, 5, 9),
    (2, 6, 15), (3, 4, 4),  (3, 6, 8),  (4, 7, 16), (5, 6, 15),
    (5, 8, 10), (6, 7, 15), (6, 8, 10), (7, 3, 6),  (7, 8, 10)
]
capacity_matrix = zeros(Int, 8, 8)
for e in flow_edges
    u, v, f = e
    add_edge!(flow_graph, u, v)
    capacity_matrix[u, v] = f
end

# 整数のルート数 = 2でデフォルトのmultiroute_flowを実行
f, F = multiroute_flow(flow_graph, 1, 8, capacity_matrix, routes = 2)

# 非整数のルート数 = 1.5でデフォルトのmultiroute_flowを実行
f, F = multiroute_flow(flow_graph, 1, 8, capacity_matrix, routes = 1.5)

# すべてのブレイキングポイント値に対してデフォルトのmultiroute_flowを実行
points = multiroute_flow(flow_graph, 1, 8, capacity_matrix)
# 次に、任意の正のルート数に対してマルチルートフローアルゴリズムを実行
f, F = multiroute_flow(points, 1.5)
f = multiroute_flow(points, 1.5, valueonly = true)

# max_flowルーチンとしてBoykov-Kolmogorovアルゴリズムを使用してマルチルートフローアルゴリズムを実行
f, F, labels = multiroute_flow(flow_graph, 1, 8, capacity_matrix,
               algorithm = BoykovKolmogorovAlgorithm(), routes = 2)

```
