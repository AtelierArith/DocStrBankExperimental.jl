```
EdgeConv(nn; aggr=max)
```

論文 [Dynamic Graph CNN for Learning on Point Clouds](https://arxiv.org/abs/1801.07829) のエッジ畳み込み層です。

次の操作を実行します。

$$
\mathbf{x}_i' = \square_{j \in N(i)}\, nn([\mathbf{x}_i; \mathbf{x}_j - \mathbf{x}_i])
$$

ここで `nn` は一般に学習可能な関数を示し、例えば線形層や多層パーセプトロンなどです。

# 引数

  * `nn`: （おそらく学習可能な）関数。
  * `aggr`: 受信メッセージの集約演算子（例： `+`, `*`, `max`, `min`, および `mean`）。

# 例:

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
x = rand(rng, Float32, in_channel, g.num_nodes)

# レイヤーを作成
l = EdgeConv(Dense(2 * in_channel, out_channel), aggr = +)

# レイヤーをセットアップ
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, ps, st)
```
