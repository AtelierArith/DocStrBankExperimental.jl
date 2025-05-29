```
GATConv(in => out, [σ; heads, concat, init, bias, negative_slope, add_self_loops])
GATConv((in, ein) => out, ...)
```

論文 [Graph Attention Networks](https://arxiv.org/abs/1710.10903) のグラフ注意層。

次の操作を実装します。

$$
\mathbf{x}_i' = \sum_{j \in N(i) \cup \{i\}} \alpha_{ij} W \mathbf{x}_j
$$

ここで、注意係数 $\alpha_{ij}$ は次のように与えられます。

$$
\alpha_{ij} = \frac{1}{z_i} \exp(LeakyReLU(\mathbf{a}^T [W \mathbf{x}_i; W \mathbf{x}_j]))
$$

$$
z_i
$$

は正規化因子です。

`ein > 0` が指定された場合、次のようにエッジ特徴の次元 `ein` がフォワードパスで期待され、注意係数は次のように計算されます。

$$
\alpha_{ij} = \frac{1}{z_i} \exp(LeakyReLU(\mathbf{a}^T [W_e \mathbf{e}_{j\to i}; W \mathbf{x}_i; W \mathbf{x}_j]))
$$

# 引数

  * `in`: 入力ノード特徴の次元。
  * `ein`: 入力エッジ特徴の次元。デフォルトは 0（すなわち、フォワードでエッジ特徴が渡されない）。
  * `out`: 出力ノード特徴の次元。
  * `σ`: 活性化関数。デフォルトは `identity`。
  * `bias`: 真の場合、加算バイアスを学習します。デフォルトは `true`。
  * `heads`: 注意ヘッドの数。デフォルトは `1`。
  * `concat`: レイヤー出力を連結するかどうか。しない場合、レイヤー出力はヘッドで平均化されます。デフォルトは `true`。
  * `negative_slope`: LeakyReLU のパラメータ。デフォルトは `0.2`。
  * `add_self_loops`: 畳み込みを行う前にグラフに自己ループを追加します。デフォルトは `true`。
  * `dropout`: 正規化された注意係数のドロップアウト確率。デフォルトは `0.0`。

# 例

```julia
# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)
x = randn(Float32, 3, g.num_nodes)

# レイヤーを作成
l = GATConv(in_channel => out_channel, add_self_loops = false, bias = false; heads=2, concat=true)

# フォワードパス
y = l(g, x)       
```
