```
min_vertex_cover(num_nodes::Int, edges::Vector{Tuple{Int, Int}}; num_layers::Int=1, driver=X)
```

グラフ `graph` の最小頂点被覆問題のインスタンスを設定するラッパー関数。

### 入力

  * `graph::PyObject`: 入力グラフで、[Python NetworkX](https://networkx.org/) グラフである必要があります。
  * `num_layers::Int=1` (オプション): 通常 $p$ で示される QAOA レイヤーの数。
  * `driver=X` (オプション): QAOA で使用されるドライバーまたはミキサー。

### 出力

  * すべての関連量を保持する `Problem` 構造体のインスタンス。

### 注意事項

最小頂点被覆問題のコスト関数は 

$$
\hat C = -\frac{3}{4} \sum_{(i, j) \in E(G)} (\hat Z_i \hat Z_j  +  \hat Z_i  +  \hat Z_j)  + \sum_{i \in V(G)} \hat Z_i,
$$

であり、ここで $E(G)$ は辺の集合、$V(G)$ は `graph` の頂点の集合です（コスト関数を *最大化* するためにグローバルなマイナス符号があります）。
