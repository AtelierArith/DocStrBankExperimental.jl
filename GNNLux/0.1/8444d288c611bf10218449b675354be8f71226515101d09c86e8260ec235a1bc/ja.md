```
GMMConv((in, ein) => out, σ=identity; K = 1, residual = false init_weight = glorot_uniform, init_bias = zeros32, use_bias = true)
```

論文[Geometric deep learning on graphs and manifolds using mixture model CNNs](https://arxiv.org/abs/1611.08402)からのグラフ混合モデル畳み込み層は、次の操作を実行します。

$$
\mathbf{x}_i' = \mathbf{x}_i + \frac{1}{|N(i)|} \sum_{j\in N(i)}\frac{1}{K}\sum_{k=1}^K \mathbf{w}_k(\mathbf{e}_{j\to i}) \odot \Theta_k \mathbf{x}_j
$$

ここで、$w^a_{k}(e^a)$は特徴`a`とカーネル`k`に対して次のように与えられます。

$$
w^a_{k}(e^a) = \exp(-\frac{1}{2}(e^a - \mu^a_k)^T (\Sigma^{-1})^a_k(e^a - \mu^a_k))
$$

$$
\Theta_k, \mu^a_k, (\Sigma^{-1})^a_k
$$

は学習可能なパラメータです。

層への入力は、サイズが`(num_features, num_nodes)`のノード特徴配列`x`と、サイズが`(num_features, num_edges)`のエッジ擬似座標配列`e`です。残差$\mathbf{x}_i$は`residual=true`の場合にのみ追加され、出力サイズは入力サイズと同じです。

# 引数

  * `in`: 入力ノード特徴の数。
  * `ein`: 入力エッジ特徴の数。
  * `out`: 出力特徴の数。
  * `σ`: 活性化関数。デフォルトは`identity`。
  * `K`: カーネルの数。デフォルトは`1`。
  * `residual`: 残差接続。デフォルトは`false`。
  * `init_weight`: 重みの初期化子。デフォルトは`glorot_uniform`。
  * `init_bias`: バイアスの初期化子。デフォルトは`zeros32`。
  * `use_bias`: 学習可能なバイアスを追加。デフォルトは`true`。

# 例

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s,t)
nin, ein, out, K = 4, 10, 7, 8 
x = randn(rng, Float32, nin, g.num_nodes)
e = randn(rng, Float32, ein, g.num_edges)

# 層を作成
l = GMMConv((nin, ein) => out, K=K)

# 層を設定
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, e, ps, st)       # サイズ:  out × num_nodes
```
