```
Tree{V} <: AbstractUnitRange{V}

Tree(tree::AbstractTree)

Tree{V}(tree::AbstractTree) where V
```

型 `V` の頂点を持つ根付き森林。この型は [indexed tree interface](https://juliacollections.github.io/AbstractTrees.jl/stable/#The-Indexed-Tree-Interface) を実装しています。
