```
VectorTransportDirection{VM<:AbstractVectorTransportMethod,RM<:AbstractRetractionMethod}
    <: AbstractVectorTransportMethod
```

指定された方向に輸送するポイントを決定するために、明示的に [`AbstractRetractionMethod`](@ref) を使用して [`AbstractVectorTransportMethod`](@ref) を使用して [`vector_transport_direction`](@ref) を指定します。これは、ベクトル輸送に関連付けられた最初の実装が暗黙的な関連付けられた再tractionを仮定した場合、非デフォルト（非暗黙的）な第二の再tractionメソッドに対してのみ必要であることに注意してください。
