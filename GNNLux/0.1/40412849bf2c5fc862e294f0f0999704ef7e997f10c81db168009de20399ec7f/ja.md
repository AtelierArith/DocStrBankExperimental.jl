```
GraphConv(in => out, σ = identity; aggr = +, init_weight = glorot_uniform,init_bias = zeros32, use_bias = true)
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
  * `init_weight`: 重みの初期化子。デフォルトは `glorot_uniform`。
  * `init_bias`: バイアスの初期化子。デフォルトは `zeros32`。
  * `use_bias`: 学習可能なバイアスを追加。デフォルトは `true`。

# 例

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)
x = randn(rng, Float32, 3, g.num_nodes)

# 層を作成
l = GraphConv(in_channel => out_channel, relu, use_bias = false, aggr = mean)

# 層をセットアップ
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, ps, st)       # 出力 y のサイズ:  5 × num_nodes
```
