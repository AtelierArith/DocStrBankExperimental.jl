```
function default_graph_sitenodes(N::Int)
```

与えられたサイトの総数 `N::Int` に基づいて、デフォルトの階層的二分木グラフと、各サイトを対応するノードにマッピングする `Dict{Int, Int2}` オブジェクトを生成します。サイトの数が2の累乗でない場合も自動的に処理します。

#### 戻り値:

  * `::Graph{Int2}`: TTN内の `N` 個のサイトに対応するデフォルトの階層的ツリーグラフ。
  * `::Dict{Int, Int2}`: 各サイトを対応するノードにマッピングします。

#### 例:

```
graph, sitenodes = default_graph_sitenodes(32)

sitenodes[1] == (1,1) # true
sitenodes[2] == (1,1) # true
sitenodes[3] == (1,2) # true
sitenodes[4] == (1,2) # true
sitenodes[31] == (1,16) # true
sitenodes[32] == (1,16) # true
```
