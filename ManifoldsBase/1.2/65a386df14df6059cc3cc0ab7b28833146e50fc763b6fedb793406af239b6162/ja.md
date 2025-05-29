```
default_vector_transport_method(M::AbstractManifold)
default_vector_transport_method(M::AbstractManifold, ::Type{T}) where {T}
```

[`AbstractVectorTransportMethod`](@ref) は、ベクトル輸送法を指定せずに [`vector_transport_to`](@ref) または [`vector_transport_direction`](@ref) を呼び出すときに使用されます。デフォルトでは、これは [`ParallelTransport`](@ref) です。

このメソッドは、`M` 上に異なるベクトル輸送法を提供する2つの異なる点の表現がある場合に、点の型 `T` でより正確に指定することもできます。
