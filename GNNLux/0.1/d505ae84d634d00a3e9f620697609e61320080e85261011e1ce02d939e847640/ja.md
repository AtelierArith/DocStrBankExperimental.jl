```
GATConv(in => out, σ = identity; heads = 1, concat = true, negative_slope = 0.2, init_weight = glorot_uniform, init_bias = zeros32, use_bias = true, add_self_loops = true, dropout=0.0)
GATConv((in, ein) => out, ...)
```

論文 [Graph Attention Networks](https://arxiv.org/abs/1710.10903) からのグラフ注意層。

次の操作を実装します。

$$
\mathbf{x}_i' = \sum_{j \in N(i) \cup \{i\}} \alpha_{ij} W \mathbf{x}_j
$$

ここで、注意係数 $\alpha_{ij}$ は次のように与えられます。

$$
\alpha_{ij} = \frac{1}{z_i} \exp(LeakyReLU(\mathbf{a}^T [W \mathbf{x}_i; W \mathbf{x}_j]))
$$

ここで、$z_i$ は正規化因子です。

`ein > 0` が指定された場合、次のようにエッジ特徴の次元 `ein` がフォワードパスで期待され、注意係数は次のように計算されます。

$$
\alpha_{ij} = \frac{1}{z_i} \exp(LeakyReLU(\mathbf{a}^T [W_e \mathbf{e}_{j\to i}; W \mathbf{x}_i; W \mathbf{x}_j]))
$$

# 引数

  * `in`: 入力ノード特徴の次元。
  * `ein`: 入力エッジ特徴の次元。デフォルトは 0（すなわち、フォワードでエッジ特徴が渡されない）。
  * `out`: 出力ノード特徴の次元。
  * `σ`: 活性化関数。デフォルトは `identity`。
  * `heads`: 注意ヘッドの数。デフォルトは `1`。
  * `concat`: レイヤー出力を連結するかどうか。しない場合、レイヤー出力はヘッド間で平均化されます。デフォルトは `true`。
  * `negative_slope`: LeakyReLU のパラメータ。デフォルトは `0.2`。
  * `init_weight`: 重みの初期化子。デフォルトは `glorot_uniform`。
  * `init_bias`: バイアスの初期化子。デフォルトは `zeros32`。
  * `use_bias`: 学習可能なバイアスを追加する。デフォルトは `true`。
  * `add_self_loops`: 畳み込みを行う前にグラフに自己ループを追加する。デフォルトは `true`。
  * `dropout`: 正規化された注意係数のドロップアウト確率。デフォルトは `0.0`。

# 例

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)
x = randn(rng, Float32, 3, g.num_nodes)

# レイヤーを作成
l = GATConv(in_channel => out_channel; add_self_loops = false, use_bias = false, heads=2, concat=true)

# レイヤーをセットアップ
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, ps, st)       
```
