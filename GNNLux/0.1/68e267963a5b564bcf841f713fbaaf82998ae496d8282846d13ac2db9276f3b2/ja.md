```
DCGRU(in => out, k; use_bias = true, init_weight = glorot_uniform, init_state = zeros32, init_bias = zeros32)
```

論文[Diffusion Convolutional Recurrent Neural Network: Data-driven Traffic Forecasting](https://arxiv.org/pdf/1707.01926)からの拡散畳み込み再帰神経ネットワーク（DCGRU）レイヤー。

空間的依存関係をモデル化するための拡散畳み込みレイヤーの後に、時間的依存関係をモデル化するためのゲート付き再帰ユニット（GRU）セルを実行します。

# 引数

  * `in`: 入力特徴の数。
  * `out`: 出力特徴の数。
  * `k`: 拡散ステップ。
  * `use_bias`: 学習可能なバイアスを追加します。デフォルトは`true`。
  * `init_weight`: 重みの初期化子。デフォルトは`glorot_uniform`。
  * `init_state`: GRUレイヤーの隠れ状態の初期状態。デフォルトは`zeros32`。
  * `init_bias`: バイアスの初期化子。デフォルトは`zeros32`。

# 例

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# データを作成
g = rand_graph(rng, 5, 10)
x = rand(rng, Float32, 2, 5)

# レイヤーを作成
l = DCGRU(2 => 5, 2)

# レイヤーを設定
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, ps, st)      # 結果のサイズ (5, 5)
```
