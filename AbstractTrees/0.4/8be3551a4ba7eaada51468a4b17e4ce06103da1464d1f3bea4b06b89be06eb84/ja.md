```
NodeType(::Type)
NodeType(node)
```

ツリーが予測可能なノードタイプを持つかどうかを指定するトレイト（`HasNodeType()`）または持たない（`NodeTypeUnknown()`）ものです。

これは `Base.IteratorEltype` に類似しています。特に [`TreeIterator`](@ref) の `IteratorEltype` はこのトレイトによって決まります。

デフォルト値は `NodeTypeUnknown()` です。
