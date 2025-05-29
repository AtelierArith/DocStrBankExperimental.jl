```
ae_init(output_dims::Array{Int64}; T::Type=Float64, method::String="xavier")
fc_init(output_dims::Array{Int64})
```

TensorFlowによって返される初期重みとバイアスの値はベクトルです。ニューラルネットワークのアーキテクチャは

$$
o_1 (\text{入力層}) \rightarrow o_2 \rightarrow \ldots \rightarrow o_n (\text{出力層})
$$

3種類のランダム初期化子が提供されています

  * `xavier`（デフォルト）。これは`tanh`完全結合ニューラルネットワークに役立ちます。

```
W^l_i \sim \sqrt{\frac{1}{n_{l-1}}}
```

  * `xavier_avg`。`xavier`の変種

$$
W^l_i \sim \sqrt{\frac{2}{n_l + n_{l-1}}}
$$

  * `he`。これは重みの活性化に配慮した初期化で、消失/爆発勾配の問題を軽減するのに役立ちます。

$$
W^l_i \sim \sqrt{\frac{2}{n_{l-1}}}
$$

# 例

```julia
x = constant(rand(10,30))
θ = ae_init([30, 20, 20, 5])
y = ae(x, [20, 20, 5], θ) # 10×5
```
