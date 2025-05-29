```
CGConv((in, ein) => out, act = identity; residual = false,
            use_bias = true, init_weight = glorot_uniform, init_bias = zeros32)
CGConv(in => out, ...)
```

論文[Crystal Graph Convolutional Neural Networks for an Accurate and Interpretable Prediction of Material Properties](https://arxiv.org/pdf/1710.10324.pdf)からのクリスタルグラフ畳み込み層。次の操作を実行します。

$$
\mathbf{x}_i' = \mathbf{x}_i + \sum_{j\in N(i)}\sigma(W_f \mathbf{z}_{ij} + \mathbf{b}_f)\, act(W_s \mathbf{z}_{ij} + \mathbf{b}_s)
$$

ここで、$\mathbf{z}_{ij}$はノードとエッジの特徴の連結$[\mathbf{x}_i; \mathbf{x}_j; \mathbf{e}_{j\to i}]$であり、$\sigma$はシグモイド関数です。残差$\mathbf{x}_i$は`residual=true`の場合にのみ追加され、出力サイズは入力サイズと同じです。

# 引数

  * `in`: 入力ノード特徴の次元。
  * `ein`: 入力エッジ特徴の次元。

`ein`が指定されていない場合、フォワードパスでエッジ特徴が入力として渡されないと仮定します。

  * `out`: 出力ノード特徴の次元。
  * `act`: 活性化関数。
  * `residual`: 残差接続を追加します。
  * `init_weight`: 重みの初期化子。デフォルトは`glorot_uniform`。
  * `init_bias`: バイアスの初期化子。デフォルトは`zeros32`。
  * `use_bias`: 学習可能なバイアスを追加します。デフォルトは`true`。

# 例

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# ランダムグラフを作成
g = rand_graph(rng, 5, 6)
x = rand(rng, Float32, 2, g.num_nodes)
e = rand(rng, Float32, 3, g.num_edges)

l = CGConv((2, 3) => 4, tanh)

# レイヤーを設定
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, e, ps, st)    # サイズ: (4, num_nodes)

# エッジ特徴なし
l = CGConv(2 => 4, tanh)
ps, st = LuxCore.setup(rng, l)
y, st = l(g, x, ps, st)    # サイズ: (4, num_nodes)
```
