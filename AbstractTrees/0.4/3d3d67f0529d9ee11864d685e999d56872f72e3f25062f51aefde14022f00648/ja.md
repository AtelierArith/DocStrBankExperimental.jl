```
nodevalue(node)
```

ツリー内のノードに関連付けられた値を取得します。これにより、[`Indexed`](@ref)や[`TreeCursor`](@ref)などのラッパーが削除されます。

デフォルトでは、この関数は恒等関数です。

**オプション**: これは、ノード自体とは別に「値」を持つノードがある任意のツリーで実装されるべきです。たとえば、整数は自体がツリーノードになれないため、「ノード」が整数であるツリーを作成するには、次のようにします。

```julia
struct IntNode
    value::Int
    children::Vector{IntNode}
end

AbstractTrees.nodevalue(n::IntNode) = n.value
```
