```
GatedGraphConv(out, num_layers; aggr=+, init=glorot_uniform)
```

[Gated Graph Sequence Neural Networks](https://arxiv.org/abs/1511.05493)からのゲーテッドグラフ畳み込み層です。

再帰を実装します。

$$
\begin{aligned}
\mathbf{h}^{(0)}_i &= [\mathbf{x}_i; \mathbf{0}] \\
\mathbf{h}^{(l)}_i &= GRU(\mathbf{h}^{(l-1)}_i, \square_{j \in N(i)} W \mathbf{h}^{(l-1)}_j)
\end{aligned}
$$

ここで、$\mathbf{h}^{(l)}_i$はGRUを通過する$l$-番目の隠れ変数を示します。入力$\mathbf{x}_i$の次元は`out`以下である必要があります。

# 引数

  * `out`: 出力特徴の次元。
  * `num_layers`: 再帰ステップの数。
  * `aggr`: 受信メッセージの集約演算子（例：`+`、`*`、`max`、`min`、および`mean`）。
  * `init`: 重み初期化関数。

# 例:

```julia
# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
out_channel = 5
num_layers = 3
g = GNNGraph(s, t)

# レイヤーを作成
l = GatedGraphConv(out_channel, num_layers)

# フォワードパス
y = l(g, x)   
```
