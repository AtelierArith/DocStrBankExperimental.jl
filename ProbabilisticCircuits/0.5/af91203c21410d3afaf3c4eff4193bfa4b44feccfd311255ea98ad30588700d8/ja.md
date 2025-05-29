```
RAT(num_features; input_func::Function = RAT_InputFunc(Literal), num_nodes_region, num_nodes_leaf, rg_depth, rg_replicas, num_nodes_root = 1, balance_childs_parents = true)
```

RAT-SPN構造を生成します。最初に、`depth`と`replicas`を持つランダムな領域グラフを生成します。次に、そのランダムな領域グラフを使用して、その領域グラフに準拠したProbCircuitを生成します。

  * `num_features`: データセット内の特徴の数、x*1...x*nを仮定
  * `input_func`: `input_func(var)`を呼び出すときに変数の新しい入力ノードを生成する関数。

ハイパーパラメータのリストは次のとおりです：

  * `rg_depth`: 領域グラフで分割を行う層の数
  * `rg_replicas`: 複製またはパーティションの数（複製はルート領域にのみ使用されます。他の領域では、1つのパーティション（内部ノード）または葉に対して0パーティションのみ）
  * `num_nodes_root`: ルート領域内の合計ノードの数
  * `num_nodes_leaf`: 各葉領域内の合計ノードの数
  * `num_nodes_region`: ルートと葉を除く各領域内の数
  * `num_splits`: 各パーティションの分割数；変数をランダムに同じサイズの領域に分割します

```
