```
ChebConv(in => out, k; bias=true, init=glorot_uniform)
```

論文[Convolutional Neural Networks on Graphs with Fast Localized Spectral Filtering](https://arxiv.org/abs/1606.09375)からのチェビシェフスペクトルグラフ畳み込み層。

実装

$$
X' = \sum^{K-1}_{k=0}  W^{(k)} Z^{(k)}
$$

ここで、$Z^{(k)}$はチェビシェフ多項式の$k$-番目の項であり、以下の再帰的な形で計算できます：

$$
\begin{aligned}
Z^{(0)} &= X \\
Z^{(1)} &= \hat{L} X \\
Z^{(k)} &= 2 \hat{L} Z^{(k-1)} - Z^{(k-2)}
\end{aligned}
$$

ここで、$\hat{L}$は[`scaled_laplacian`](@ref)です。

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `k`: チェビシェフ多項式の次数。
  * `bias`: 学習可能なバイアスを追加。
  * `init`: 重みの初期化方法。

# 例

```julia
# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s, t)
x = randn(Float32, 3, g.num_nodes)

# レイヤーを作成
l = ChebConv(3 => 5, 5) 

# フォワードパス
y = l(g, x)       # サイズ:  5 × num_nodes
```
