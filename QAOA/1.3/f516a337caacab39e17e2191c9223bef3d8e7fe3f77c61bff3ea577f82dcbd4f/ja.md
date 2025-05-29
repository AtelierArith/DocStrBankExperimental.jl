```
max_cut(num_nodes::Int, edges::Vector{Tuple{Int, Int}}; num_layers::Int=1, driver=X)
```

グラフ `graph` の MaxCut 問題のインスタンスを設定するラッパー関数。

### 入力

  * `graph::PyObject`: 入力グラフで、[Python NetworkX](https://networkx.org/) グラフでなければなりません。
  * `num_layers::Int=1` (オプション): 通常 $p$ で示される QAOA レイヤーの数。
  * `driver=X` (オプション): QAOA で使用されるドライバーまたはミキサー。

### 出力

  * すべての関連量を保持する `Problem` 構造体のインスタンス。

### 注意事項

MaxCut 問題のコスト関数は、[元の QAOA 論文](https://arxiv.org/abs/1411.4028) で定義されているように、

$$
\hat C = -\frac{1}{2} \sum_{(i, j) \in E(G)} \hat Z_i \hat Z_j + \mathrm{const.},
$$

ここで $E(G)$ はグラフ $G$ の辺の集合です。 ```
