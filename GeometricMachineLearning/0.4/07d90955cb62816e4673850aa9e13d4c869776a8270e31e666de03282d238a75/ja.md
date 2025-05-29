```
ZygotePullback <: AbstractPullback
```

[`Zygote`](https://github.com/FluxML/Zygote.jl) バックエンドに基づくプルバック。

# 例

入力のみに基づいて訓練されたネットワークの場合：

```jldoctest
using GeometricMachineLearning
using GeometricMachineLearning: _processing

loss = AutoEncoderLoss()
_pullback = ZygotePullback(loss)
nn = NeuralNetwork(Chain(Dense(10, 2, tanh), Dense(2, 10, tanh)))
input = rand(10)
_pullback(nn.params, nn.model, input)[2](1) |> _processing |> typeof

# 出力

@NamedTuple{L1::@NamedTuple{W::Matrix{Float64}, b::Vector{Float64}}, L2::@NamedTuple{W::Matrix{Float64}, b::Vector{Float64}}}
```

この例では [`_processing`](@ref) が `Zygote` の特異性を回避するために使用されています。
