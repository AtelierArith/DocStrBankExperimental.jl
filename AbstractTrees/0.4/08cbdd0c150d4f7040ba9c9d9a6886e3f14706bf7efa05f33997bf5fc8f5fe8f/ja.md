```
ParentLinks(::Type{T})
ParentLinks(tree)
```

ツリーのノードがその親への参照を格納しているか（`StoredParents()`）、または親がツリー構造から推測されなければならないか（`ImplicitParents()`）を示すトレイトです。

`ParentLinks` が `StoredParents()` を返すツリーは *MUST* [`parent`](@ref) を実装しなければなりません。

`StoredParents()` の場合、ツリー内のすべてのノードも `StoredParents()` を持たなければならず、そうでない場合は `ImplicitParents()` を使用してください。

**オプション**: ノードの親が格納されている場合、ツリーに対してこれを実装する必要があります。

```julia
AbstractTrees.ParentLinks(::Type{<:TreeType}) = AbstractTrees.StoredParents()
parent(t::TreeType) = get_parent(t)
```
