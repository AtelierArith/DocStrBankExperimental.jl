```
GraphConv(in => out, σ=identity; aggr=+, bias=true, init=glorot_uniform)
```

参照文献からのグラフ畳み込み層: [Weisfeiler and Leman Go Neural: Higher-order Graph Neural Networks](https://arxiv.org/abs/1810.02244)。

実行内容:

$$
\mathbf{x}_i' = W_1 \mathbf{x}_i + \square_{j \in \mathcal{N}(i)} W_2 \mathbf{x}_j
$$

ここで、集約タイプは `aggr` によって選択されます。

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `σ`: 活性化関数。
  * `aggr`: 受信メッセージの集約演算子（例: `+`, `*`, `max`, `min`, および `mean`）。
  * `bias`: 学習可能なバイアスを追加。
  * `init`: 重みの初期化子。

# 例

```julia
# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)
x = randn(Float32, 3, g.num_nodes)

# レイヤーを作成
l = GraphConv(in_channel => out_channel, relu, bias = false, aggr = mean)

# フォワードパス
y = l(g, x)       
```
