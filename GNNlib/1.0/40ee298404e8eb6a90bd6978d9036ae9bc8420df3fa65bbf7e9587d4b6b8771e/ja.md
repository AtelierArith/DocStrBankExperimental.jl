```
softmax_edge_neighbors(g, e)
```

エッジ特徴 `e` の各ノードの隣接領域に対するソフトマックス。

$$
\mathbf{e}'_{j\to i} = \frac{e^{\mathbf{e}_{j\to i}}}
                    {\sum_{j'\in N(i)} e^{\mathbf{e}_{j'\to i}}}.
$$
