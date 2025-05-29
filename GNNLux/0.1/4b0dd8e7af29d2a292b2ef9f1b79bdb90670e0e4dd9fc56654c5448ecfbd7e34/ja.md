```
EGNNConv((in, ein) => out; hidden_size=2in, residual=false)
EGNNConv(in => out; hidden_size=2in, residual=false)
```

[E(n)等変グラフニューラルネットワーク](https://arxiv.org/abs/2102.09844)からの等変グラフ畳み込み層。

この層は次の操作を実行します：

$$
\begin{aligned}
\mathbf{m}_{j\to i} &=\phi_e(\mathbf{h}_i, \mathbf{h}_j, \lVert\mathbf{x}_i-\mathbf{x}_j\rVert^2, \mathbf{e}_{j\to i}),\\
\mathbf{x}_i' &= \mathbf{x}_i + C_i\sum_{j\in\mathcal{N}(i)}(\mathbf{x}_i-\mathbf{x}_j)\phi_x(\mathbf{m}_{j\to i}),\\
\mathbf{m}_i &= C_i\sum_{j\in\mathcal{N}(i)} \mathbf{m}_{j\to i},\\
\mathbf{h}_i' &= \mathbf{h}_i + \phi_h(\mathbf{h}_i, \mathbf{m}_i)
\end{aligned}
$$

ここで、$\mathbf{h}_i$, $\mathbf{x}_i$, $\mathbf{e}_{j\to i}$は不変ノード特徴、等変ノード特徴、およびエッジ特徴です。$\phi_e$, $\phi_h$, および$\phi_x$は二層のMLPです。`C`は正規化のための定数で、$1/|\mathcal{N}(i)|$として計算されます。

# コンストラクタ引数

  * `in`: `h`の入力特徴の数。
  * `out`: `h`の出力特徴の数。
  * `ein`: 入力エッジ特徴の数。
  * `hidden_size`: 隠れ表現のサイズ。
  * `residual`: `true`の場合、残差接続を追加します。`in == out`の場合のみ可能です。デフォルトは`false`です。

# フォワードパス

```
l(g, x, h, e=nothing, ps, st)
```

## フォワードパス引数：

  * `g` : グラフ。
  * `x` : 等変ノード座標の行列。
  * `h` : 不変ノード特徴の行列。
  * `e` : 不変エッジ特徴の行列。デフォルトは`nothing`。
  * `ps` : パラメータ。
  * `st` : 状態。

更新された`h`と`x`を返します。

# 例

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# ランダムグラフを作成
g = rand_graph(rng, 10, 10)
h = randn(rng, Float32, 5, g.num_nodes)
x = randn(rng, Float32, 3, g.num_nodes)

egnn = EGNNConv(5 => 6, 10)

# 層を設定
ps, st = LuxCore.setup(rng, egnn)

# フォワードパス
(hnew, xnew), st = egnn(g, h, x, ps, st)
```
