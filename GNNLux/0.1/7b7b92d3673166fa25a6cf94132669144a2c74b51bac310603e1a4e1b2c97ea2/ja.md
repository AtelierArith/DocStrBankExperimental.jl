```
DConv(in => out, k; init_weight = glorot_uniform, init_bias = zeros32, use_bias = true)
```

論文[Diffusion Convolutional Recurrent Neural Networks: Data-Driven Traffic Forecasting](https://arxiv.org/pdf/1707.01926)からの拡散畳み込み層。

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `k`: 拡散ステップの数。
  * `init_weight`: 重みの初期化子。デフォルトは`glorot_uniform`。
  * `init_bias`: バイアスの初期化子。デフォルトは`zeros32`。
  * `use_bias`: 学習可能なバイアスを追加するか。デフォルトは`true`。

# 例

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# ランダムグラフを作成
g = GNNGraph(rand(rng, 10, 10), ndata = rand(rng, Float32, 2, 10))

dconv = DConv(2 => 4, 4)

# レイヤーを設定
ps, st = LuxCore.setup(rng, dconv)

# フォワードパス
y, st = dconv(g, g.ndata.x, ps, st)   # サイズ: (4, num_nodes)
```
