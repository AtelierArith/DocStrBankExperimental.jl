```
Tree{V} <: AbstractUnitRange{V}

Tree(tree::AbstractTree)

Tree{V}(tree::AbstractTree) where V
```

A rooted forest with vertices of type `V`. This type implements the [indexed tree interface](https://juliacollections.github.io/AbstractTrees.jl/stable/#The-Indexed-Tree-Interface).
