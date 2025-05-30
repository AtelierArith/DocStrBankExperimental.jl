```
ParentLinks(::Type{T})
ParentLinks(tree)
```

ノードが親への参照を格納しているかどうかを示すトレイト（`StoredParents()`）または、親がツリー構造から推測されなければならないかどうかを示す（`ImplicitParents()`）。

`ParentLinks` が `StoredParents()` を返すツリーは *MUST* [`parent`](@ref) を実装しなければなりません。

`StoredParents()` の場合、ツリー内のすべてのノードも `StoredParents()` を持たなければなりません。そうでない場合は `ImplicitParents()` を使用してください。

**OPTIONAL**: ノードの親が格納されている場合、ツリーに対してこれを実装する必要があります。

```julia
AbstractTrees.ParentLinks(::Type{<:TreeType}) = AbstractTrees.StoredParents()
parent(t::TreeType) = get_parent(t)
```
