```
Composite(primitives...)
Composite(default_rule, primitives...)
```

自動的に合成プリミティブを順次適用することでLRPルールのリストを構築します。

# プリミティブ

単一のルールを適用するには、次のようにします：

  * [`LayerMap`](@ref) を使用してモデルの `n` 番目の層にルールを適用します
  * [`GlobalMap`](@ref) を使用してすべての層にルールを適用します
  * [`RangeMap`](@ref) を使用して層の位置範囲にルールを適用します
  * [`FirstLayerMap`](@ref) を使用して最初の層にルールを適用します
  * [`LastLayerMap`](@ref) を使用して最後の層にルールを適用します

層のタイプに基づいてルールのセットを適用するには、次のようにします：

  * [`GlobalTypeMap`](@ref) を使用して層のタイプをLRPルールにマッピングする辞書を適用します
  * [`RangeTypeMap`](@ref) を使用して一般化された範囲に対する `TypeMap` を適用します
  * [`FirstLayerTypeMap`](@ref) を使用してモデルの最初の層に対する `TypeMap` を適用します
  * [`LastLayerTypeMap`](@ref) を使用して最後の層に対する `TypeMap` を適用します
  * [`FirstNTypeMap`](@ref) を使用して最初の `n` 層に対する `TypeMap` を適用します

# 例

VGG11モデルを使用した場合：

```julia-repl
julia> composite = Composite(
           GlobalTypeMap(
               ConvLayer => AlphaBetaRule(),
               Dense => EpsilonRule(),
               PoolingLayer => EpsilonRule(),
               DropoutLayer => PassRule(),
               ReshapingLayer => PassRule(),
           ),
           FirstNTypeMap(7, Conv => FlatRule()),
       );

julia> analyzer = LRP(model, composite)
LRP(
  Conv((3, 3), 3 => 64, relu, pad=1)    => FlatRule(),
  MaxPool((2, 2))                       => EpsilonRule{Float32}(1.0f-6),
  Conv((3, 3), 64 => 128, relu, pad=1)  => FlatRule(),
  MaxPool((2, 2))                       => EpsilonRule{Float32}(1.0f-6),
  Conv((3, 3), 128 => 256, relu, pad=1) => FlatRule(),
  Conv((3, 3), 256 => 256, relu, pad=1) => FlatRule(),
  MaxPool((2, 2))                       => EpsilonRule{Float32}(1.0f-6),
  Conv((3, 3), 256 => 512, relu, pad=1) => AlphaBetaRule{Float32}(2.0f0, 1.0f0),
  Conv((3, 3), 512 => 512, relu, pad=1) => AlphaBetaRule{Float32}(2.0f0, 1.0f0),
  MaxPool((2, 2))                       => EpsilonRule{Float32}(1.0f-6),
  Conv((3, 3), 512 => 512, relu, pad=1) => AlphaBetaRule{Float32}(2.0f0, 1.0f0),
  Conv((3, 3), 512 => 512, relu, pad=1) => AlphaBetaRule{Float32}(2.0f0, 1.0f0),
  MaxPool((2, 2))                       => EpsilonRule{Float32}(1.0f-6),
  MLUtils.flatten                       => PassRule(),
  Dense(25088 => 4096, relu)            => EpsilonRule{Float32}(1.0f-6),
  Dropout(0.5)                          => PassRule(),
  Dense(4096 => 4096, relu)             => EpsilonRule{Float32}(1.0f-6),
  Dropout(0.5)                          => PassRule(),
  Dense(4096 => 1000)                   => EpsilonRule{Float32}(1.0f-6),
)
```
