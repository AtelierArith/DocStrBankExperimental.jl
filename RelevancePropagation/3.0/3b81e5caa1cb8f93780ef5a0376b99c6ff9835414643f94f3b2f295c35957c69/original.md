```
EpsilonAlpha2Beta1Flat(; [epsilon=1.0f-6])
```

Composite using the following primitives:

```julia-repl
julia> EpsilonAlpha2Beta1Flat()
Composite(
  GlobalTypeMap(  # all layers
    Flux.Conv               => RelevancePropagation.AlphaBetaRule{Float32}(2.0f0, 1.0f0),
    Flux.ConvTranspose      => RelevancePropagation.AlphaBetaRule{Float32}(2.0f0, 1.0f0),
    Flux.CrossCor           => RelevancePropagation.AlphaBetaRule{Float32}(2.0f0, 1.0f0),
    Flux.Dense              => RelevancePropagation.EpsilonRule{Float32}(1.0f-6),
    Flux.Scale              => RelevancePropagation.EpsilonRule{Float32}(1.0f-6),
    Flux.LayerNorm          => RelevancePropagation.LayerNormRule(),
    typeof(NNlib.dropout)   => RelevancePropagation.PassRule(),
    Flux.AlphaDropout       => RelevancePropagation.PassRule(),
    Flux.Dropout            => RelevancePropagation.PassRule(),
    Flux.BatchNorm          => RelevancePropagation.PassRule(),
    typeof(Flux.flatten)    => RelevancePropagation.PassRule(),
    typeof(MLUtils.flatten) => RelevancePropagation.PassRule(),
    typeof(identity)        => RelevancePropagation.PassRule(),
 ),
  FirstLayerTypeMap(  # first layer
    Flux.Conv          => RelevancePropagation.FlatRule(),
    Flux.ConvTranspose => RelevancePropagation.FlatRule(),
    Flux.CrossCor      => RelevancePropagation.FlatRule(),
 ),
)
```
