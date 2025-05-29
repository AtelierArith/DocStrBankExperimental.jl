```
GCNConv(in => out, σ=identity; [init_weight, init_bias, use_bias, add_self_loops, use_edge_weight])
```

論文 [Semi-supervised Classification with Graph Convolutional Networks](https://arxiv.org/abs/1609.02907) のグラフ畳み込み層です。

次の操作を実行します。

$$
\mathbf{x}'_i = \sum_{j\in N(i)} a_{ij} W \mathbf{x}_j
$$

ここで、$a_{ij} = 1 / \sqrt{|N(i)||N(j)|}$ はノードの次数から計算された正規化因子です。

入力グラフに重み付きエッジがあり、`use_edge_weight=true` の場合、$a_{ij}$ は次のように計算されます。

$$
a_{ij} = \frac{e_{j\to i}}{\sqrt{\sum_{j \in N(i)}  e_{j\to i}} \sqrt{\sum_{i \in N(j)}  e_{i\to j}}}
$$

# 引数

  * `in`: 入力特徴量の数。
  * `out`: 出力特徴量の数。
  * `σ`: 活性化関数。デフォルトは `identity`。
  * `init_weight`: 重みの初期化子。デフォルトは `glorot_uniform`。
  * `init_bias`: バイアスの初期化子。デフォルトは `zeros32`。
  * `use_bias`: 学習可能なバイアスを追加する。デフォルトは `true`。
  * `add_self_loops`: 畳み込みを行う前にグラフに自己ループを追加する。デフォルトは `false`。
  * `use_edge_weight`: `true` の場合、入力グラフのエッジ重みを考慮する（利用可能な場合）。 `add_self_loops=true` の場合、新しい重みは 1 に設定されます。 このオプションは、フォワードパスで `edge_weight` が明示的に提供されている場合は無視されます。デフォルトは `false`。

# フォワード

```
(::GCNConv)(g, x, [edge_weight], ps, st; norm_fn = d -> 1 ./ sqrt.(d), conv_weight=nothing)
```

グラフ `g`、サイズ `[in, num_nodes]` のノード特徴行列 `x`、オプションでエッジ重みベクトルとレイヤーのパラメータおよび状態を入力として受け取ります。サイズ `[out, num_nodes]` のノード特徴行列を返します。

`norm_fn` パラメータは、関数を引数として渡すことでグラフ畳み込み操作のカスタム正規化を可能にします。 デフォルトでは、各ノードの次数 (`d`) の逆平方根である $\frac{1}{\sqrt{d}}$ を計算します。 `conv_weight` がサイズ `[out, in]` の `AbstractMatrix` の場合、その重み行列を使用して畳み込みが実行されます。

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
l = GCNConv(3 => 5) 

# レイヤーをセットアップ
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y = l(g, x, ps, st)       # 出力の最初のエントリのサイズ:  5 × num_nodes

# エッジ重みとカスタム正規化関数を使用した畳み込み
w = [1.1, 0.1, 2.3, 0.5]
custom_norm_fn(d) = 1 ./ sqrt.(d + 1)  # カスタム正規化関数
y = l(g, x, w, ps, st; norm_fn = custom_norm_fn)

# エッジ重みはグラフに埋め込むこともできます。
g = GNNGraph(s, t, w)
l = GCNConv(3 => 5, use_edge_weight=true)
ps, st = Lux.setup(rng, l)
y = l(g, x, ps, st) # l(g, x, w) と同じ 
```
