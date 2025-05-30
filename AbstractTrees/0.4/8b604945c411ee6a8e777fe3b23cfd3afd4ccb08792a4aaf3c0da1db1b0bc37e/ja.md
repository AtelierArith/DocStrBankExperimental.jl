```
SiblingLinks(::Type{T})
SiblingLinks(tree)
```

ノードがその兄弟への参照を格納しているかどうかを示すトレイト（`StoredSiblings()`）またはツリー構造から推測しなければならない（`ImplicitSiblings()`）ことを示します。

ノードがトレイト `StoredSiblings()` を持っている場合、ツリー内のすべての接続されたノードもそうでなければなりません。そうでない場合は、代わりに `ImplicitSiblings()` を使用してください。

**オプション**: ノードの兄弟が格納されている場合、ツリーに対してこれを実装する必要があります。

```julia
AbstractTrees.SiblingLinks(::Type{<:TreeType}) = AbstractTrees.StoredSiblings()
```
