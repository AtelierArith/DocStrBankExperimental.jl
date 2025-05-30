```
ChildIndexing(::Type{N})
ChildIndexing(node)
```

子ノード `n` が子を持つかどうかを示すトレイトであり（[`children`](@ref) によって返される）、1-based インデックスを使用してインデックス付けできるかどうかを示します。オプションは [`NonIndexedChildren`](@ref)（デフォルト）または [`IndexedChildren`](@ref) のいずれかです。

ツリー `TreeType` が子に対して1-based インデックスをサポートすることを宣言するには、次のように定義します。

```julia
AbstractTrees.ChildIndexing(::Type{<:TreeType}) = AbstractTrees.IndexedChildren()
```

ノードが `IndexedChildren()` を持っている場合、ツリー内のすべての接続されたノードもそうでなければなりません。そうでない場合は、代わりに `NonIndexedChildren()` を使用してください。
