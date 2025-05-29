```
GConvLSTM(in => out, k; use_bias = true, init_weight = glorot_uniform, init_state = zeros32, init_bias = zeros32)
```

グラフ畳み込み長短期記憶（GConvLSTM）再帰層は、論文 [Structured Sequence Modeling with Graph Convolutional Recurrent Networks](https://arxiv.org/pdf/1612.07659) に基づいています。

空間的依存関係をモデル化するために ChebConv の層を実行し、その後、時間的依存関係をモデル化するために長短期記憶（LSTM）セルを使用します。

# 引数

  * `in`: 入力特徴量の数。
  * `out`: 出力特徴量の数。
  * `k`: チェビシェフ多項式の次数。
  * `use_bias`: 学習可能なバイアスを追加します。デフォルトは `true`。
  * `init_weight`: 重みの初期化子。デフォルトは `glorot_uniform`。
  * `init_state`: GRU層の隠れ状態の初期状態。デフォルトは `zeros32`。
  * `init_bias`: バイアスの初期化子。デフォルトは `zeros32`。

# 例

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# データを作成
g = rand_graph(rng, 5, 10)
x = rand(rng, Float32, 2, 5)

# GConvLSTM層を作成
l = GConvLSTM(2 => 5, 2)

# 層を設定
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, ps, st)      # 結果のサイズ (5, 5)
```
