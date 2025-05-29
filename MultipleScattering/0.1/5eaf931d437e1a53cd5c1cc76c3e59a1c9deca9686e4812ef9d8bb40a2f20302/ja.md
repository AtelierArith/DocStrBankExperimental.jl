次を参照してください: [`ContinuousImpulse`](@ref), [`frequency_to_time`](@ref), [`DiscreteGaussianImpulse`](@ref)

```
DiscreteImpulse{T<:AbstractFloat}
```

数値インパルスを表すために使用される構造体です。この構造体を`frequency_to_time`関数で使用するために必要なフィールドは、周波数応答ベクトルである`in_freq`と周波数ベクトル`ω`のみです。
