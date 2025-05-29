```
multiroute_flow(flow_graph, source, target[, DefaultCapacity][, flow_algorithm][, mrf_algorithm][, routes])
```

汎用の multiroute_flow 関数。

出力は入力に応じて異なります：

  * `route` の数が `0` の場合、multiroute flow のブレークポイントのセットを返します。
  * `route` の数が `1` の場合、1-不連続パスのセットを持つフローを返します（これは古典的な最大フローの実装です）。
  * 入力がブレークポイントのセットとルート値 `k` に制限されている場合、k-ルートフローのみを返します。
  * それ以外の場合、1) 最大フローと 2) フローマトリックスのタプルを返します。最大フローのサブルーチンが Boykov-Kolmogorov アルゴリズムである場合、関連する最小カットが3番目の出力として返されます。

入力がネットワークの場合、次の引数が必要です：

  * `flow_graph`: 入力グラフ
  * `source`: ソース頂点
  * `target`: ターゲット頂点
  * `capacity_matrix`: エッジフロー容量の行列
  * `flow_algorithm`: フローアルゴリズムのキーワード引数
  * `mrf_algorithm`: マルチルートフローアルゴリズムのキーワード引数
  * `routes`: ルートの数のキーワード引数

入力が (ブレーク) ポイントのセットとルートの数のみの場合、次の引数が必要です：

  * `breakingpoints`: ブレークポイントのベクトル
  * `routes`: ルートの数

入力が (ブレーク) ポイントのセット、ルートの数、およびネットワーク記述子の場合、次の引数が必要です：

  * `breakingpoints`: ブレークポイントのベクトル
  * `routes`: ルートの数
  * `flow_graph`: 入力グラフ
  * `source`: ソース頂点
  * `target`: ターゲット頂点
  * `capacity_matrix`: エッジフロー容量の行列
  * `flow_algorithm`: フローアルゴリズムのキーワード引数

関数はデフォルトで Push-relabel（古典的フロー）および Kishimoto（マルチルート）アルゴリズムを使用します。代わりに、使用するアルゴリズムもキーワード引数を通じて指定できます。容量行列が提供されていない場合、各リンクのデフォルト容量は `1` と見なされます。

`mrf_algorithm` キーワードは次の場合に拡張マルチルートフローに強制されます：

  * ルートの数が非整数である
  * ルートの数が 0 または未指定である

### 使用例：

（フローアルゴリズムおよび容量行列に関するオプションについては、[`maximum_flow`](@ref) セクションを参照してください）

```julia
julia> flow_graph = lg.DiGraph(8) # フローグラフを作成

julia> flow_edges = [
(1, 2, 10), (1, 3, 5),  (1, 4, 15), (2, 3, 4),  (2, 5, 9),
(2, 6, 15), (3, 4, 4),  (3, 6, 8),  (4, 7, 16), (5, 6, 15),
(5, 8, 10), (6, 7, 15), (6, 8, 10), (7, 3, 6),  (7, 8, 10)
]

julia> capacity_matrix = zeros(Int, 8, 8) # 容量行列を作成

julia> for e in flow_edges
    u, v, f = e
    add_edge!(flow_graph, u, v)
    capacity_matrix[u, v] = f
end

julia> f, F = multiroute_flow(flow_graph, 1, 8, capacity_matrix, routes = 2) # 整数のルート数 = 2 でデフォルトの multiroute_flow を実行

julia> f, F = multiroute_flow(flow_graph, 1, 8, capacity_matrix, routes = 1.5) # 非整数のルート数 = 1.5 でデフォルトの multiroute_flow を実行

julia> points = multiroute_flow(flow_graph, 1, 8, capacity_matrix) # すべてのブレークポイント値に対してデフォルトの multiroute_flow を実行

julia> f, F = multiroute_flow(points, 1.5) # 任意の正のルート数に対してマルチルートフローアルゴリズムを実行

julia> f = multiroute_flow(points, 1.5, valueonly = true)

julia> f, F, labels = multiroute_flow(flow_graph, 1, 8, capacity_matrix, algorithm = BoykovKolmogorovAlgorithm(), routes = 2) # Boykov-Kolmogorov アルゴリズムを最大フローのルーチンとして使用してマルチルートフローアルゴリズムを実行

```
