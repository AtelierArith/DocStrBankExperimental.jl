```
default_retraction_method(M::AbstractManifold)
default_retraction_method(M::AbstractManifold, ::Type{T}) where {T}
```

[`AbstractRetractionMethod`](@ref)は、再tractionメソッドを指定せずに[`retract`](@ref)を呼び出すときに使用されます。デフォルトでは、これは[`ExponentialRetraction`](@ref)です。

このメソッドは、`M`上に異なる再tractionメソッドを提供する2つの異なる点の表現がある場合に、点の型`T`を使用してより正確に指定することもできます。
