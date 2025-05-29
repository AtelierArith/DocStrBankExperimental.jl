```
A3TGCN(in => out; use_bias = true, init_weight = glorot_uniform, init_state = zeros32, init_bias = zeros32, add_self_loops = false, use_edge_weight = true)
```

論文 [A3T-GCN: Attention Temporal Graph Convolutional Network for Traffic Forecasting](https://arxiv.org/pdf/2006.11583.pdf) からの注意付き時間グラフ畳み込みネットワーク (A3T-GCN) モデル。

TGCN レイヤーを実行し、その後にソフトアテンションレイヤーを続けます。

# 引数

  * `in`: 入力特徴量の数。
  * `out`: 出力特徴量の数。
  * `use_bias`: 学習可能なバイアスを追加します。デフォルトは `true`。
  * `init_weight`: 重みの初期化子。デフォルトは `glorot_uniform`。
  * `init_state`: GRU レイヤーの隠れ状態の初期状態。デフォルトは `zeros32`。
  * `init_bias`: バイアスの初期化子。デフォルトは `zeros32`。
  * `add_self_loops`: 畳み込みを行う前にグラフに自己ループを追加します。デフォルトは `false`。
  * `use_edge_weight`: `true` の場合、入力グラフのエッジ重みを考慮します（利用可能な場合）。                     `add_self_loops=true` の場合、新しい重みは 1 に設定されます。                     このオプションは、フォワードパスで `edge_weight` が明示的に提供されている場合は無視されます。                     デフォルトは `false`。

# 例

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# データを作成
g = rand_graph(rng, 5, 10)
x = rand(rng, Float32, 2, 5)

# A3TGCN レイヤーを作成
l = A3TGCN(2 => 6)

# レイヤーを設定
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, ps, st)      # 結果のサイズ (6, 5)
```
