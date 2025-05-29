```
GINConv(f, ϵ; aggr=+)
```

論文[How Powerful are Graph Neural Networks?](https://arxiv.org/pdf/1810.00826.pdf)からのグラフ同型性畳み込み層。

グラフ畳み込みを実装します。

$$
\mathbf{x}_i' = f_\Theta\left((1 + \epsilon) \mathbf{x}_i + \sum_{j \in N(i)} \mathbf{x}_j \right)
$$

ここで、$f_\Theta$は通常、学習可能な関数を示し、例えば線形層や多層パーセプトロンです。

# 引数

  * `f`: ノード特徴に作用する（学習可能な）関数。
  * `ϵ`: 重み付け係数。

# 例:

```julia
# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)

# 密な層を作成
nn = Dense(in_channel, out_channel)

# 層を作成
l = GINConv(nn, 0.01f0, aggr = mean)

# フォワードパス
y = l(g, x)  
```
