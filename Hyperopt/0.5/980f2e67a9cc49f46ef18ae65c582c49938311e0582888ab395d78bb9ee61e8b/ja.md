```
RandomSampler{T<:AbstractRNG} <: Sampler
```

各パラメータの値を候補ベクトルから一様にランダムにサンプリングします。対数一様サンプリングは、対数間隔の候補ベクトルを提供することで利用可能です。

オプションで、初期化のために `AbstractRNG` を渡すことができます。
