```
default_inverse_retraction_method(M::AbstractManifold)
default_inverse_retraction_method(M::AbstractManifold, ::Type{T}) where {T}
```

[`AbstractInverseRetractionMethod`](@ref) は、逆射影法を指定せずに[`inverse_retract`](@ref)を呼び出すときに使用されます。デフォルトでは、これは[`LogarithmicInverseRetraction`](@ref)です。

このメソッドは、`M`上に異なる逆射影法を提供する2つの異なる点の表現がある場合に、点の型`T`を指定することでより正確に指定することもできます。
