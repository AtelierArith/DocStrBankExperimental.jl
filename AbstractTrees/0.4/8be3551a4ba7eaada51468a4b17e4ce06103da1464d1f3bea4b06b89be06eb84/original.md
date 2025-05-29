```
NodeType(::Type)
NodeType(node)
```

A trait which specifies whether a tree has a predictable node type (`HasNodeType()`) or not (`NodeTypeUnknown()`).

This is analogous to `Base.IteratorEltype`.  In particular the `IteratorEltype` of [`TreeIterator`](@ref) is dictated by this trait.

The default value is `NodeTypeUnknown()`.
