```
GCNConv(in => out, σ=identity; [bias, init, add_self_loops, use_edge_weight])
```

論文 [Semi-supervised Classification with Graph Convolutional Networks](https://arxiv.org/abs/1609.02907) のグラフ畳み込み層です。

次の操作を実行します。

$$
\mathbf{x}'_i = \sum_{j\in N(i)} a_{ij} W \mathbf{x}_j
$$

ここで、$a_{ij} = 1 / \sqrt{|N(i)||N(j)|}$ はノードの次数から計算される正規化因子です。

入力グラフに重み付きエッジがあり、`use_edge_weight=true` の場合、$a_{ij}$ は次のように計算されます。

$$
a_{ij} = \frac{e_{j\to i}}{\sqrt{\sum_{j \in N(i)}  e_{j\to i}} \sqrt{\sum_{i \in N(j)}  e_{i\to j}}}
$$

レイヤーへの入力は、サイズ `(num_features, num_nodes)` のノード特徴配列 `X` とオプションでエッジ重みベクトルです。

# 引数

  * `in`: 入力特徴の数。
  * `out`: 出力特徴の数。
  * `σ`: 活性化関数。デフォルトは `identity`。
  * `bias`: 学習可能なバイアスを追加。デフォルトは `true`。
  * `init`: 重みの初期化子。デフォルトは `glorot_uniform`。
  * `add_self_loops`: 畳み込みを行う前にグラフに自己ループを追加。デフォルトは `false`。
  * `use_edge_weight`: `true` の場合、入力グラフのエッジ重みを考慮します（利用可能な場合）。 `add_self_loops=true` の場合、新しい重みは 1 に設定されます。このオプションは、フォワードパスで `edge_weight` が明示的に提供されている場合は無視されます。デフォルトは `false`。

# フォワード

```
(::GCNConv)(g::GNNGraph, x, edge_weight = nothing; norm_fn = d -> 1 ./ sqrt.(d), conv_weight = nothing) -> AbstractMatrix
```

グラフ `g`、サイズ `[in, num_nodes]` のノード特徴行列 `x`、およびオプションでエッジ重みベクトルを入力として受け取ります。サイズ `[out, num_nodes]` のノード特徴行列を返します。

`norm_fn` パラメータは、関数を引数として渡すことにより、グラフ畳み込み操作のカスタム正規化を可能にします。デフォルトでは、各ノードの次数 (`d`) の逆平方根である $\frac{1}{\sqrt{d}}$ を計算します。`conv_weight` がサイズ `[out, in]` の `AbstractMatrix` の場合、その重み行列を使用して畳み込みが実行され、モデルに保存されている重みは使用されません。

# 例

```julia
# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s, t)
x = randn(Float32, 3, g.num_nodes)

# レイヤーを作成
l = GCNConv(3 => 5) 

# フォワードパス
y = l(g, x)       # サイズ:  5 × num_nodes

# エッジ重みとカスタム正規化関数を使用した畳み込み
w = [1.1, 0.1, 2.3, 0.5]
custom_norm_fn(d) = 1 ./ sqrt.(d + 1)  # カスタム正規化関数
y = l(g, x, w; norm_fn = custom_norm_fn)

# エッジ重みはグラフに埋め込むこともできます。
g = GNNGraph(s, t, w)
l = GCNConv(3 => 5, use_edge_weight=true) 
y = l(g, x) # l(g, x, w) と同じ 
```
