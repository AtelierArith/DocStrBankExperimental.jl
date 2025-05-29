```
has_components(M::AbstractManifold)
```

[`AbstractManifold`](@ref)`(M)`が、反復可能なコンポーネントを持つかどうかを返します。例えば、[`PowerManifold`](@ref)や[`ProductManifold`](@ref)のようなものです。デフォルトでは、この関数は`false`を返します。
