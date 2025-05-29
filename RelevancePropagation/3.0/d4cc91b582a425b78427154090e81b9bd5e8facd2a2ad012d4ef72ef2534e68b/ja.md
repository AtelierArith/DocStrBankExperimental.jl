```
EpsilonPlus(; [epsilon=1.0f-6])
```

次のプリミティブを使用して合成します：

```julia-repl
julia> EpsilonPlus()
Composite(
  GlobalTypeMap(  # すべてのレイヤー
    Flux.Conv               => RelevancePropagation.ZPlusRule(),
    Flux.ConvTranspose      => RelevancePropagation.ZPlusRule(),
    Flux.CrossCor           => RelevancePropagation.ZPlusRule(),
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
)
```
