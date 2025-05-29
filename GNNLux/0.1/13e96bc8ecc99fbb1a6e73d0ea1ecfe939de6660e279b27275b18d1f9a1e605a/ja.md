```
ResGatedGraphConv(in => out, act=identity; init_weight = glorot_uniform, init_bias = zeros32, use_bias = true)
```

[Residual Gated Graph ConvNets](https://arxiv.org/abs/1711.07553) 論文からの残差ゲート付きグラフ畳み込み演算子です。

レイヤーのフォワードパスは次のように与えられます。

$$
\mathbf{x}_i' = act\big(U\mathbf{x}_i + \sum_{j \in N(i)} \eta_{ij} V \mathbf{x}_j\big),
$$

ここで、エッジゲート $\eta_{ij}$ は次のように与えられます。

$$
\eta_{ij} = sigmoid(A\mathbf{x}_i + B\mathbf{x}_j).
$$

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `act`: 活性化関数。
  * `init_weight`: 重みの初期化子。デフォルトは `glorot_uniform`。
  * `init_bias`: バイアスの初期化子。デフォルトは `zeros32`。
  * `use_bias`: 学習可能なバイアスを追加するか。デフォルトは `true`。

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
x = randn(rng, Float32, in_channel, g.num_nodes)

# レイヤーを作成
l = ResGatedGraphConv(in_channel => out_channel, tanh, use_bias = true)

# レイヤーをセットアップ
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, ps, st)       # サイズ:  out_channel × num_nodes  
```
