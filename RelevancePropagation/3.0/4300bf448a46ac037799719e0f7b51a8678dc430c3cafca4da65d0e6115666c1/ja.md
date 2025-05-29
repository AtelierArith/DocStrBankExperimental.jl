```
EpsilonGammaBox(low, high; [epsilon=1.0f-6, gamma=0.25f0])
```

次のプリミティブを使用して合成します：

```julia-repl
julia> EpsilonGammaBox(-3.0f0, 3.0f0)
Composite(
  GlobalTypeMap(  # すべてのレイヤー
    Flux.Conv               => RelevancePropagation.GammaRule{Float32}(0.25f0),
    Flux.ConvTranspose      => RelevancePropagation.GammaRule{Float32}(0.25f0),
    Flux.CrossCor           => RelevancePropagation.GammaRule{Float32}(0.25f0),
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
  FirstLayerTypeMap(  # 最初のレイヤー
    Flux.Conv          => RelevancePropagation.ZBoxRule{Float32}(-3.0f0, 3.0f0),
    Flux.ConvTranspose => RelevancePropagation.ZBoxRule{Float32}(-3.0f0, 3.0f0),
    Flux.CrossCor      => RelevancePropagation.ZBoxRule{Float32}(-3.0f0, 3.0f0),
 ),
)
```
