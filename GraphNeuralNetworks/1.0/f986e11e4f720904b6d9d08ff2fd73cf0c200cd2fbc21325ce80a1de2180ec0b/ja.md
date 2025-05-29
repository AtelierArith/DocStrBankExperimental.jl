```
EdgeConv(nn; aggr=max)
```

論文 [Dynamic Graph CNN for Learning on Point Clouds](https://arxiv.org/abs/1801.07829) のエッジ畳み込み層。

次の操作を実行します。

$$
\mathbf{x}_i' = \square_{j \in N(i)}\, nn([\mathbf{x}_i; \mathbf{x}_j - \mathbf{x}_i])
$$

ここで `nn` は一般に学習可能な関数を示し、例えば線形層や多層パーセプトロンです。

# 引数

  * `nn`: （学習可能な）関数。
  * `aggr`: 受信メッセージの集約演算子（例：`+`、`*`、`max`、`min`、`mean`）。

# 例:

```julia
# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)

# レイヤーを作成
l = EdgeConv(Dense(2 * in_channel, out_channel), aggr = +)

# フォワードパス
y = l(g, x)
```
