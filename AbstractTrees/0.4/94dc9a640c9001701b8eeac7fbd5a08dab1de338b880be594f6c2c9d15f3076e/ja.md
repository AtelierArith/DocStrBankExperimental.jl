```
ImplicitCursor{N,P,S} <: TreeCursor{N,P}
```

ノードに直接親または兄弟に効率的にアクセスできない [`TreeCursor`](@ref) です。これは「最悪のシナリオ」のツリーカーソルと考えるべきです。特に、`ImplicitCursor` は型 `S` の子の反復状態を格納し、`ImplicitCursor` のメソッドが型安定であるためには、子の反復状態の型を推論できる必要があります。詳細は [`childstatetype`](@ref) を参照してください。
