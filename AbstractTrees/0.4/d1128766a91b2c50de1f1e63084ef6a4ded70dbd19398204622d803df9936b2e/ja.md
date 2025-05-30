```
TrivialCursor{N,P} <: TreeCursor{N,P}
```

この[`TreeCursor`](@ref)は、基になるノードの機能と一致します。このカーソルでラップされたツリーノードは、`TreeCursor`に必要なほとんどの機能を持っており、この型は他の`TreeCursor`オブジェクトとの完全に一貫したインターフェースを維持するためだけに存在します。
