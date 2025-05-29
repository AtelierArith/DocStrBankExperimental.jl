```
NNConv(in => out, f, σ=identity; aggr=+, init_bias = zeros32, use_bias = true, init_weight = glorot_uniform)
```

[Neural Message Passing for Quantum Chemistry](https://arxiv.org/abs/1704.01212) 論文からの連続カーネルベースの畳み込み演算子です。この畳み込みは、[Dynamic Edge-Conditioned Filters in Convolutional Neural Networks on Graphs](https://arxiv.org/abs/1704.02901) 論文からのエッジ条件付き畳み込みとしても知られています。

次の操作を実行します。

$$
\mathbf{x}_i' = W \mathbf{x}_i + \square_{j \in N(i)} f_\Theta(\mathbf{e}_{j\to i})\,\mathbf{x}_j
$$

ここで、$f_\Theta$ は学習可能な関数（例えば、線形層や多層パーセプトロン）を示します。サイズが `(num_edge_features, num_edges)` のバッチエッジ特徴 `e` の入力が与えられると、関数 `f` はサイズが `(out, in, num_edges)` のバッチ行列配列を返します。便利のため、単一の `(out*in, num_edges)` 行列を返す関数も許可されています。

# 引数

  * `in`: 入力ノード特徴の次元。
  * `out`: 出力ノード特徴の次元。
  * `f`: エッジ特徴に作用する（学習可能な）関数。
  * `aggr`: 受信メッセージの集約演算子（例：`+`、`*`、`max`、`min`、および `mean`）。
  * `σ`: 活性化関数。
  * `init_weight`: 重みの初期化子。デフォルトは `glorot_uniform`。
  * `init_bias`: バイアスの初期化子。デフォルトは `zeros32`。
  * `use_bias`: 学習可能なバイアスを追加。デフォルトは `true`。

# 例:

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# データを作成
n_in = 3
n_in_edge = 10
n_out = 5

s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s, t)
x = randn(rng, Float32, n_in, g.num_nodes)
e = randn(rng, Float32, n_in_edge, g.num_edges)

# 密な層を作成
nn = Dense(n_in_edge => n_out * n_in)

# 層を作成
l = NNConv(n_in => n_out, nn, tanh, use_bias = true, aggr = +)

# 層をセットアップ
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, e, ps, st)       # サイズ:  n_out × num_nodes 
```
