```
mean(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::GeodesicInterpolation;
    shuffle_rng=nothing,
    retraction::AbstractRetractionMethod = default_retraction_method(M, eltype(x)),
    inverse_retraction::AbstractInverseRetractionMethod = default_inverse_retraction_method(M, eltype(x)),
    kwargs...,
)
```

`x`のリーマン中心を、繰り返し重み付き測地線補間を使用してオンライン方式で推定します。詳細については、[`GeodesicInterpolation`](@extref `ManifoldsBase.GeodesicInterpolation`)を参照してください。

`shuffle_rng`が提供されている場合、平均を計算するために考慮される点の順序をシャッフルするために使用されます。

オプションで、（逆）再tractionを指定するために`retraction`および`inverse_retraction`メソッドタイプを渡すことができます。
