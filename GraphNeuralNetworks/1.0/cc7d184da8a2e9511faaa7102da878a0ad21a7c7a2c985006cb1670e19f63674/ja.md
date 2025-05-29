```
Set2Set(n_in, n_iters, n_layers = 1)
```

論文 [Order Matters: Sequence to sequence for sets](https://arxiv.org/abs/1511.06391) の Set2Set レイヤー。

バッチ内の各グラフに対して、このレイヤーは以下のステップを `n_iters` 回繰り返すことによってサイズ `2*n_in` の出力ベクトルを計算します：

$$
\mathbf{q} = \mathrm{LSTM}(\mathbf{q}_{t-1}^*)
\alpha_{i} = \frac{\exp(\mathbf{q}^T \mathbf{x}_i)}{\sum_{j=1}^N \exp(\mathbf{q}^T \mathbf{x}_j)} 
\mathbf{r} = \sum_{i=1}^N \alpha_{i} \mathbf{x}_i
\mathbf{q}^*_t = [\mathbf{q}; \mathbf{r}]
$$

ここで `N` はグラフ内のノードの数、`LSTM` は `n_layers` 層を持つ長短期記憶ネットワークで、入力サイズは `2*n_in`、出力サイズは `n_in` です。

グラフのバッチ `g` とノード特徴 `x` が与えられた場合、このレイヤーはサイズ `(2*n_in, n_graphs)` の行列を返します。```
