```
ChebConv(in => out, k; init_weight = glorot_uniform, init_bias = zeros32, use_bias = true)
```

論文 [Convolutional Neural Networks on Graphs with Fast Localized Spectral Filtering](https://arxiv.org/abs/1606.09375) に基づくチェビシェフスペクトルグラフ畳み込み層です。

実装内容

$$
X' = \sum^{K-1}_{k=0}  W^{(k)} Z^{(k)}
$$

ここで、$Z^{(k)}$ はチェビシェフ多項式の $k$ 番目の項であり、以下の再帰的な形で計算できます：

$$
\begin{aligned}
Z^{(0)} &= X \\
Z^{(1)} &= \hat{L} X \\
Z^{(k)} &= 2 \hat{L} Z^{(k-1)} - Z^{(k-2)}
\end{aligned}
$$

ここで、$\hat{L}$ は [`scaled_laplacian`](@ref) です。

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `k`: チェビシェフ多項式の次数。
  * `init_weight`: 重みの初期化子。デフォルトは `glorot_uniform`。
  * `init_bias`: バイアスの初期化子。デフォルトは `zeros32`。
  * `use_bias`: 学習可能なバイアスを追加するか。デフォルトは `true`。

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
l = ChebConv(3 => 5, 5)

# レイヤーをセットアップ
ps, st = LuxCore.setup(rng, l)

# フォワードパス
y, st = l(g, x, ps, st)       # 出力 y のサイズ:  5 × num_nodes
```
