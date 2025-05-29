```
ResGatedGraphConv(in => out, act=identity; init=glorot_uniform, bias=true)
```

[Residual Gated Graph ConvNets](https://arxiv.org/abs/1711.07553) 論文からの残差ゲート付きグラフ畳み込み演算子です。

レイヤーのフォワードパスは次のように与えられます。

$$
\mathbf{x}_i' = act\big(U\mathbf{x}_i + \sum_{j \in N(i)} \eta_{ij} V \mathbf{x}_j\big),
$$

ここで、エッジゲート $\eta_{ij}$ は次のように与えられます。

$$
\eta_{ij} = sigmoid(A\mathbf{x}_i + B\mathbf{x}_j).
$$

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `act`: 活性化関数。
  * `init`: 重み行列の初期化関数。
  * `bias`: true の場合、加算バイアスを学習します。

# 例:

```julia
# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)

# レイヤーを作成
l = ResGatedGraphConv(in_channel => out_channel, tanh, bias = true)

# フォワードパス
y = l(g, x)  
```
