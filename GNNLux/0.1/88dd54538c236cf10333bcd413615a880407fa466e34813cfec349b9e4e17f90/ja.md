```
AGNNConv(; init_beta=1.0f0, trainable=true, add_self_loops=true)
```

論文[Attention-based Graph Neural Network for Semi-Supervised Learning](https://arxiv.org/abs/1803.03735)からの注意ベースのグラフニューラルネットワーク層です。

フォワードパスは次のように与えられます。

$$
\mathbf{x}_i' = \sum_{j \in N(i)} \alpha_{ij} \mathbf{x}_j
$$

ここで、注意係数$\alpha_{ij}$は次のように与えられます。

$$
\alpha_{ij} =\frac{e^{\beta \cos(\mathbf{x}_i, \mathbf{x}_j)}}
                  {\sum_{j'}e^{\beta \cos(\mathbf{x}_i, \mathbf{x}_{j'})}}
$$

コサイン距離は次のように定義されます。

$$
\cos(\mathbf{x}_i, \mathbf{x}_j) = 
  \frac{\mathbf{x}_i \cdot \mathbf{x}_j}{\lVert\mathbf{x}_i\rVert \lVert\mathbf{x}_j\rVert}
$$

そして、$\beta$は`trainable=true`の場合に学習可能なパラメータです。

# 引数

  * `init_beta`: $\beta$の初期値。デフォルトは1.0f0。
  * `trainable`: trueの場合、$\beta$は学習可能です。デフォルトは`true`。
  * `add_self_loops`: 畳み込みを行う前にグラフに自己ループを追加します。デフォルトは`true`。

# 例:

```julia
using GNNLux, Lux, Random

# ランダム数生成器を初期化
rng = Random.default_rng()

# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s, t)

# レイヤーを作成
l = AGNNConv(init_beta=2.0f0)

# レイヤーをセットアップ
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, ps, st)   
```
