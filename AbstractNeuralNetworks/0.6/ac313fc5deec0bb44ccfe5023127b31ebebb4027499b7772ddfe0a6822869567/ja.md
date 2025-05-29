```
NetworkLoss
```

すべてのニューラルネットワーク損失のための抽象型です。 `CustomLoss <: NetworkLoss` を実装したい場合は、ファンクタを定義する必要があります：

```julia
(loss::CustomLoss)(model, ps, input, output)
```

ここで `model` は `AbstractExplicitLayer` または `Chain` のインスタンスであり、`ps` はパラメータです。

例として [`FeedForwardLoss`](@ref)、`GeometricMachineLearning.TransformerLoss`、`GeometricMachineLearning.AutoEncoderLoss` および `GeometricMachineLearning.ReducedLoss` を参照してください。
