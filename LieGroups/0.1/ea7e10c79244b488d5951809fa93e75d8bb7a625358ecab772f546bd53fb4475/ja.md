```
AbstractMultiplicationGroupOperation <: AbstractGroupOperation
```

デフォルトを導入して実現される群演算で、例えば `_compose(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, a, b) = a * b` のように `*` がオーバーロードされることにフォールバックします。
