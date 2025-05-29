```
GATv2Conv(in => out, σ = identity; heads = 1, concat = true, negative_slope = 0.2, init_weight = glorot_uniform, init_bias = zeros32, use_bias = true, add_self_loops = true, dropout=0.0)
GATv2Conv((in, ein) => out, ...)
```

論文[How Attentive are Graph Attention Networks?](https://arxiv.org/abs/2105.14491)からのGATv2注意層。

次の操作を実装します。

$$
\mathbf{x}_i' = \sum_{j \in N(i) \cup \{i\}} \alpha_{ij} W_1 \mathbf{x}_j
$$

ここで、注意係数$\alpha_{ij}$は次のように与えられます。

$$
\alpha_{ij} = \frac{1}{z_i} \exp(\mathbf{a}^T LeakyReLU(W_2 \mathbf{x}_i + W_1 \mathbf{x}_j))
$$

$$
z_i
$$

は正規化因子です。

`ein > 0`が指定された場合、次のようにエッジ特徴の次元`ein`がフォワードパスで期待され、注意係数は次のように計算されます。

$$
\alpha_{ij} = \frac{1}{z_i} \exp(\mathbf{a}^T LeakyReLU(W_3 \mathbf{e}_{j\to i} + W_2 \mathbf{x}_i + W_1 \mathbf{x}_j)).
$$

# 引数

  * `in`: 入力ノード特徴の次元。
  * `ein`: 入力エッジ特徴の次元。デフォルトは0（すなわち、フォワードでエッジ特徴は渡されない）。
  * `out`: 出力ノード特徴の次元。
  * `σ`: 活性化関数。デフォルトは`identity`。
  * `heads`: 注意ヘッドの数。デフォルトは`1`。
  * `concat`: レイヤー出力を連結するかどうか。しない場合、レイヤー出力はヘッドで平均化される。デフォルトは`true`。
  * `negative_slope`: LeakyReLUのパラメータ。デフォルトは`0.2`。
  * `add_self_loops`: 畳み込みを行う前にグラフに自己ループを追加する。デフォルトは`true`。
  * `dropout`: 正規化された注意係数のドロップアウト確率。デフォルトは`0.0`。
  * `init_weight`: 重みの初期化子。デフォルトは`glorot_uniform`。
  * `init_bias`: バイアスの初期化子。デフォルトは`zeros32`。
  * `use_bias`: 学習可能なバイアスを追加する。デフォルトは`true`。

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
ein = 3
g = GNNGraph(s, t)
x = randn(rng, Float32, 3, g.num_nodes)

# レイヤーを作成
l = GATv2Conv((in_channel, ein) => out_channel, add_self_loops = false)

# レイヤーをセットアップ
ps, st = LuxCore.setup(rng, l)

# エッジ特徴
e = randn(rng, Float32, ein, length(s))

# フォワードパス
y, st = l(g, x, e, ps, st)    
```
