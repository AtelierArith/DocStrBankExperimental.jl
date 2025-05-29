```
typetree_mmd(T, TT; rem = false)
```

Return a `Vector{String}` of the type hierarchy with type `T`, in format suitable for making [Mermaid](https://github.com/mermaid-js/mermaid) class diagrams. For the root case (where `T` is the top of the hierarchy), `TT` may be set to nothing (default argument).

The keyword argument `rem` can be set to true to strip the module prefix from typenames. This is useful for Mermaid diagrams, because the Mermaid classDiagram does not currently support "." characters in class names.

# Examples

```julia
# the following may be pasted into the Mermaid live editor:
# https://mermaid.live/
print(join(typetree_mmd(Integer), ""))
```
