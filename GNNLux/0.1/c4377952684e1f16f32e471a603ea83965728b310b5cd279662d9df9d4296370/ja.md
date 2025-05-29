```
TGCN(in => out; use_bias = true, init_weight = glorot_uniform, init_state = zeros32, init_bias = zeros32, add_self_loops = false, use_edge_weight = true)
```

論文[T-GCN: A Temporal Graph Convolutional Network for Traffic Prediction](https://arxiv.org/pdf/1811.05320.pdf)からの時間的グラフ畳み込みネットワーク（T-GCN）再帰層。

空間的依存関係をモデル化するためにGCNConvの層を実行し、その後、時間的依存関係をモデル化するためにゲート付き再帰ユニット（GRU）セルを使用します。

# 引数

  * `in`: 入力特徴の数。
  * `out`: 出力特徴の数。
  * `use_bias`: 学習可能なバイアスを追加します。デフォルトは`true`。
  * `init_weight`: 重みの初期化子。デフォルトは`glorot_uniform`。
  * `init_state`: GRU層の隠れ状態の初期状態。デフォルトは`zeros32`。
  * `init_bias`: バイアスの初期化子。デフォルトは`zeros32`。
  * `add_self_loops`: 畳み込みを実行する前にグラフに自己ループを追加します。デフォルトは`false`。
  * `use_edge_weight`: `true`の場合、入力グラフのエッジ重みを考慮します（利用可能な場合）。                    `add_self_loops=true`の場合、新しい重みは1に設定されます。                     このオプションは、フォワードパスで`edge_weight`が明示的に提供されている場合は無視されます。                    デフォルトは`false`。

# 例

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# データを作成
g = rand_graph(rng, 5, 10)
x = rand(rng, Float32, 2, 5)

# TGCN層を作成
tgcn = TGCN(2 => 6)

# 層を設定
ps, st = LuxCore.setup(rng, tgcn)

# フォワードパス
y, st = tgcn(g, x, ps, st)      # 結果のサイズ (6, 5)
```
