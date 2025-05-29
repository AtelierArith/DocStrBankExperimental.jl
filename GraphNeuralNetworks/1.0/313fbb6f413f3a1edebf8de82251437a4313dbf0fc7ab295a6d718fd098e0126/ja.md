```
DConv(ch::Pair{Int, Int}, k::Int; init = glorot_uniform, bias = true)
```

論文 [Diffusion Convolutional Recurrent Neural Networks: Data-Driven Traffic Forecasting](https://arxiv.org/pdf/1707.01926) に基づく拡散畳み込み層。

# 引数

  * `ch`: 入力および出力の次元のペア。
  * `k`: 拡散ステップの数。
  * `init`: 重みの初期化子。デフォルトは `glorot_uniform`。
  * `bias`: 学習可能なバイアスを追加。デフォルトは `true`。

# 例

```
julia> g = GNNGraph(rand(10, 10), ndata = rand(Float32, 2, 10));

julia> dconv = DConv(2 => 4, 4)
DConv(2 => 4, 4)

julia> y = dconv(g, g.ndata.x);

julia> size(y)
(4, 10)
```
