```
TrivialCursor{N,P} <: TreeCursor{N,P}
```

[`TreeCursor`](@ref) の機能に一致する、基になるノードの機能を持つ。 このカーソルでラップされたツリーノードは、`TreeCursor` に必要な機能のほとんどを持っており、この型は他の `TreeCursor` オブジェクトとの完全に一貫したインターフェースを維持するためだけに存在する。
