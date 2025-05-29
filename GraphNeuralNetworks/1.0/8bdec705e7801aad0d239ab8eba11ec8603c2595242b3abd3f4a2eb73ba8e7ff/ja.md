```
TransformerConv((in, ein) => out; [heads, concat, init, add_self_loops, bias_qkv,
    bias_root, root_weight, gating, skip_connection, batch_norm, ff_channels]))
```

[Masked Label Prediction: Unified Message Passing Model for Semi-Supervised  Classification](https://arxiv.org/abs/2009.03509) 論文からのトランスフォーマーのようなマルチヘッドアテンション畳み込み演算子で、エッジ特徴も考慮しています。さらに、[Attention, Learn to Solve Routing Problems!](https://arxiv.org/abs/1706.03762) 論文からのトランスフォーマーのような畳み込み演算子としても構成できるオプションが含まれており、連続的なフィードフォワードネットワークやスキップレイヤー、バッチ正規化も含まれています。

レイヤーの基本的なフォワードパスは次のように与えられます。

$$
x_i' = W_1x_i + \sum_{j\in N(i)} \alpha_{ij} (W_2 x_j + W_6e_{ij})
$$

ここで、アテンションスコアは次のようになります。

$$
\alpha_{ij} = \mathrm{softmax}\left(\frac{(W_3x_i)^T(W_4x_j+
W_6e_{ij})}{\sqrt{d}}\right).
$$

オプションとして、ゲーティングメカニズムを介して変換されたルートノード特徴との集約値の組み合わせを次のように行うことができます。

$$
x'_i = \beta_i W_1 x_i + (1 - \beta_i) \underbrace{\left(\sum_{j \in \mathcal{N}(i)}
\alpha_{i,j} W_2 x_j \right)}_{=m_i}
$$

ここで、

$$
\beta_i = \textrm{sigmoid}(W_5^{\top} [ W_1 x_i, m_i, W_1 x_i - m_i ]).
$$

が使用されます。

# 引数

  * `in`: 入力特徴の次元で、出力特徴の次元にも対応します。
  * `ein`: エッジ特徴の次元; 0の場合、エッジ特徴は使用されません。
  * `out`: 出力の次元。
  * `heads`: 出力のヘッド数。デフォルトは `1`。
  * `concat`: レイヤー出力を連結するかどうか。そうでない場合、レイヤー出力はヘッド間で平均化されます。デフォルトは `true`。
  * `init`: 重み行列の初期化関数。デフォルトは `glorot_uniform`。
  * `add_self_loops`: 入力グラフに自己ループを追加します。デフォルトは `false`。
  * `bias_qkv`: 設定されている場合、ノードのキー、クエリ、値の変換にバイアスが使用されます。デフォルトは `true`。
  * `bias_root`: 設定されている場合、ルート重みが使用されるときにレイヤーはルートのための加算バイアスも学習します。デフォルトは `true`。
  * `root_weight`: 設定されている場合、レイヤーは変換されたルートノード特徴を出力に追加します。デフォルトは `true`。
  * `gating`: 設定されている場合、ゲーティングメカニズムによって集約と変換されたルートノード特徴を組み合わせます。デフォルトは `false`。
  * `skip_connection`: 設定されている場合、入力からスキップ接続が行われ、出力に追加されます。デフォルトは `false`。
  * `batch_norm`: 設定されている場合、出力にバッチ正規化が適用されます。デフォルトは `false`。
  * `ff_channels`: 正の値の場合、フィードフォワードNNが追加され、最初の隠れノード数は指定された数になります。このNNも、該当するパラメータが設定されている場合、スキップ接続とバッチ正規化を取得します。デフォルト: `0`。

# 例

```julia
N, in_channel, out_channel = 4, 3, 5
ein, heads = 2, 3
g = GNNGraph([1,1,2,4], [2,3,1,1])
l = TransformerConv((in_channel, ein) => in_channel; heads, gating = true, bias_qkv = true)
x = rand(Float32, in_channel, N)
e = rand(Float32, ein, g.num_edges)
l(g, x, e)
```
