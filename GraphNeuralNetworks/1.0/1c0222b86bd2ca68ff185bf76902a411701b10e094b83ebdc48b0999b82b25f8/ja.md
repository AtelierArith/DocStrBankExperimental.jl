```
SAGEConv(in => out, σ=identity; aggr=mean, bias=true, init=glorot_uniform)
```

論文[Inductive Representation Learning on Large Graphs](https://arxiv.org/pdf/1706.02216.pdf)からのGraphSAGE畳み込み層。

実行します：

$$
\mathbf{x}_i' = W \cdot [\mathbf{x}_i; \square_{j \in \mathcal{N}(i)} \mathbf{x}_j]
$$

ここで、集約タイプは`aggr`によって選択されます。

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `σ`: 活性化関数。
  * `aggr`: 受信メッセージの集約演算子（例：`+`、`*`、`max`、`min`、および`mean`）。
  * `bias`: 学習可能なバイアスを追加。
  * `init`: 重みの初期化子。

# 例：

```julia
# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)

# レイヤーを作成
l = SAGEConv(in_channel => out_channel, tanh, bias = false, aggr = +)

# フォワードパス
y = l(g, x)   
```
