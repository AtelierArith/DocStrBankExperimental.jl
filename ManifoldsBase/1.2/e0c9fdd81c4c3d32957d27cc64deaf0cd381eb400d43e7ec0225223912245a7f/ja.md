```
VectorTransportTo{VM<:AbstractVectorTransportMethod,RM<:AbstractRetractionMethod}
    <: AbstractVectorTransportMethod
```

[`vector_transport_to`](@ref)を指定し、[`AbstractVectorTransportMethod`](@ref)を使用して、[`AbstractInverseRetractionMethod`](@ref)を明示的に使用して、`p`から`q`への輸送方向を決定します。これは、ベクトル輸送に関連する非デフォルト（非暗黙的）な第二の再tractionメソッドにのみ必要であることに注意してください。すなわち、最初の実装が暗黙的な関連再tractionを仮定した場合です。
