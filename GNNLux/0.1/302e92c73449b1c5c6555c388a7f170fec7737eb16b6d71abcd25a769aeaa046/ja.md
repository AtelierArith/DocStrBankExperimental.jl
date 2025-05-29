```
SAGEConv(in => out, σ=identity; aggr=mean, init_weight = glorot_uniform, init_bias = zeros32, use_bias=true)
```

論文[Inductive Representation Learning on Large Graphs](https://arxiv.org/pdf/1706.02216.pdf)からのGraphSAGE畳み込み層。

実行します：

$$
\mathbf{x}_i' = W \cdot [\mathbf{x}_i; \square_{j \in \mathcal{N}(i)} \mathbf{x}_j]
$$

ここで、集約タイプは`aggr`によって選択されます。

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `σ`: 活性化関数。
  * `aggr`: 受信メッセージの集約演算子（例：`+`、`*`、`max`、`min`、および`mean`）。
  * `init_bias`: バイアス初期化子。デフォルトは`zeros32`。
  * `use_bias`: 学習可能なバイアスを追加します。デフォルトは`true`。

# 例：

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
l = SAGEConv(in_channel => out_channel, tanh, use_bias = false, aggr = +)

# レイヤーをセットアップ
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, ps, st)       # サイズ:  out_channel × num_nodes   
```
