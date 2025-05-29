```
Composite(primitives...)
Composite(default_rule, primitives...)
```

Automatically contructs a list of LRP-rules by sequentially applying composite primitives.

# Primitives

To apply a single rule, use:

  * [`LayerMap`](@ref) to apply a rule to the `n`-th layer of a model
  * [`GlobalMap`](@ref) to apply a rule to all layers
  * [`RangeMap`](@ref) to apply a rule to a positional range of layers
  * [`FirstLayerMap`](@ref) to apply a rule to the first layer
  * [`LastLayerMap`](@ref) to apply a rule to the last layer

To apply a set of rules to layers based on their type, use:

  * [`GlobalTypeMap`](@ref) to apply a dictionary that maps layer types to LRP-rules
  * [`RangeTypeMap`](@ref) for a `TypeMap` on generalized ranges
  * [`FirstLayerTypeMap`](@ref) for a `TypeMap` on the first layer of a model
  * [`LastLayerTypeMap`](@ref) for a `TypeMap` on the last layer
  * [`FirstNTypeMap`](@ref) for a `TypeMap` on the first `n` layers

# Example

Using a VGG11 model:

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
