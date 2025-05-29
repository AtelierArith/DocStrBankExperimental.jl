```
EvolveGCNO(ch; use_bias = true, init_weight = glorot_uniform, init_state = zeros32, init_bias = zeros32)
```

論文 [EvolveGCN: Evolving Graph Convolutional Networks for Dynamic Graphs](https://arxiv.org/pdf/1902.10191) からの進化グラフ畳み込みネットワーク (EvolveGCNO) レイヤー。

時間的グラフのスナップショットにわたって、長短期記憶 (LSTM) レイヤーから導出されたパラメータを使用してグラフ畳み込みレイヤーを実行します。

# 引数

  * `in`: 入力特徴量の数。
  * `out`: 出力特徴量の数。
  * `use_bias`: 学習可能なバイアスを追加します。デフォルトは `true`。
  * `init_weight`: 重みの初期化子。デフォルトは `glorot_uniform`。
  * `init_state`: GRU レイヤーの隠れ状態の初期状態。デフォルトは `zeros32`。
  * `init_bias`: バイアスの初期化子。デフォルトは `zeros32`。

# 例

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# データを作成
tg = TemporalSnapshotsGNNGraph([rand_graph(rng, 10, 20; ndata = rand(rng, 4, 10)), rand_graph(rng, 10, 14; ndata = rand(rng, 4, 10)), rand_graph(rng, 10, 22; ndata = rand(rng, 4, 10))])

# レイヤーを作成
l = EvolveGCNO(4 => 5)

# レイヤーをセットアップ
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(tg, tg.ndata.x , ps, st)      # 結果のサイズ 3, サイズ y[1] (5, 10)
```
