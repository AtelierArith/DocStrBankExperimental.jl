```
CGConv((in, ein) => out, act=identity; bias=true, init=glorot_uniform, residual=false)
CGConv(in => out, ...)
```

論文 [Crystal Graph Convolutional Neural Networks for an Accurate and Interpretable Prediction of Material Properties](https://arxiv.org/pdf/1710.10324.pdf) のクリスタルグラフ畳み込み層。次の操作を実行します。

$$
\mathbf{x}_i' = \mathbf{x}_i + \sum_{j\in N(i)}\sigma(W_f \mathbf{z}_{ij} + \mathbf{b}_f)\, act(W_s \mathbf{z}_{ij} + \mathbf{b}_s)
$$

ここで、$\mathbf{z}_{ij}$ はノードとエッジの特徴の連結 $[\mathbf{x}_i; \mathbf{x}_j; \mathbf{e}_{j\to i}]$ であり、$\sigma$ はシグモイド関数です。残差 $\mathbf{x}_i$ は `residual=true` の場合のみ追加され、出力サイズは入力サイズと同じです。

# 引数

  * `in`: 入力ノード特徴の次元。
  * `ein`: 入力エッジ特徴の次元。

`ein` が指定されていない場合、フォワードパスでエッジ特徴が入力として渡されないと仮定します。

  * `out`: 出力ノード特徴の次元。
  * `act`: 活性化関数。
  * `bias`: 学習可能なバイアスを追加。
  * `init`: 重みの初期化子。
  * `residual`: 残差接続を追加。

# 例

```julia
g = rand_graph(5, 6)
x = rand(Float32, 2, g.num_nodes)
e = rand(Float32, 3, g.num_edges)

l = CGConv((2, 3) => 4, tanh)
y = l(g, x, e)    # size: (4, num_nodes)

# エッジ特徴なし
l = CGConv(2 => 4, tanh)
y = l(g, x)    # size: (4, num_nodes)
```
