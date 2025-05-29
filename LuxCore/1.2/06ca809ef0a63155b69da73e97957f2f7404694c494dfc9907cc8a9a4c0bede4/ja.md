```
abstract type AbstractLuxWrapperLayer{layer} <: AbstractLuxLayer
```

詳細なドキュメントについては[`AbstractLuxContainerLayer`](@ref)を参照してください。この抽象型は[`AbstractLuxContainerLayer`](@ref)に非常に似ていますが、単一のレイヤーをコンテナにラップすることを許可します。

さらに、[`initialparameters`](@ref)および[`initialstates`](@ref)を呼び出すと、パラメータと状態はフィールドと同じ名前の`NamedTuple`に**ラップされません**。

便宜上、`(::AbstractLuxWrapperLayer)(x, ps, st)`というフォールバック呼び出しを定義しており、これは`getfield(x, layer)(x, ps, st)`を呼び出します。
