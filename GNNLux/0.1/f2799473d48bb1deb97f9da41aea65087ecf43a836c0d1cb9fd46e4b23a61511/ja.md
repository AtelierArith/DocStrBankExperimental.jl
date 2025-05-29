```
SGConv(int => out, k = 1; init_weight = glorot_uniform, init_bias = zeros32, use_bias = true, add_self_loops = true,use_edge_weight = false)
```

[グラフ畳み込みネットワークの簡素化](https://arxiv.org/pdf/1902.07153.pdf)からのSGC層は、次の操作を実行します。

$$
H^{K} = (\tilde{D}^{-1/2} \tilde{A} \tilde{D}^{-1/2})^K X \Theta
$$

ここで、$\tilde{A}$は$A + I$です。

# 引数

  * `in`: 入力特徴量の数。
  * `out`: 出力特徴量の数。
  * `k` : ホップの数k。デフォルトは`1`。
  * `add_self_loops`: 畳み込みを行う前にグラフに自己ループを追加します。デフォルトは`false`。
  * `use_edge_weight`: `true`の場合、入力グラフのエッジ重みを考慮します（利用可能な場合）。`add_self_loops=true`の場合、新しい重みは1に設定されます。デフォルトは`false`。
  * `init_weight`: 重みの初期化子。デフォルトは`glorot_uniform`。
  * `init_bias`: バイアスの初期化子。デフォルトは`zeros32`。
  * `use_bias`: 学習可能なバイアスを追加します。デフォルトは`true`。

# 例

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s, t)
x = randn(rng, Float32, 3, g.num_nodes)

# レイヤーを作成
l = SGConv(3 => 5; add_self_loops = true) 

# レイヤーをセットアップ
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, ps, st)       # サイズ:  5 × num_nodes

# エッジ重みを使った畳み込み
w = [1.1, 0.1, 2.3, 0.5]
y = l(g, x, w, ps, st)

# エッジ重みはグラフに埋め込むこともできます。
g = GNNGraph(s, t, w)
l = SGConv(3 => 5, add_self_loops = true, use_edge_weight=true) 
ps, st = LuxCore.setup(rng, l)
y, st = l(g, x, ps, st) # l(g, x, w)と同じ 
```
