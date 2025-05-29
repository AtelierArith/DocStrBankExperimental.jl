```
repr_tree(tree; context=nothing, kw...)
repr_tree(f, tree; context=nothing, kw...)
repr_tree(f, g, tree; context=nothing, kw...)
```

Get the string result of calling [`print_tree`](@ref) with the supplied arguments.

The `context` argument works as it does in `Base.repr`.
