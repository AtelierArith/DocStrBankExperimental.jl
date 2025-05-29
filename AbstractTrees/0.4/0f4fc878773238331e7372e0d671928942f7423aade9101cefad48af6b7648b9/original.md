```
TreeIterator{T}
```

An iterator of a tree that implements the AbstractTrees interface.  Every `TreeIterator` is simply a wrapper of an [`IteratorState`](@ref) which fully determine the iteration state and implement their own alternative protocol using [`next`](@ref).

## Constructors

All `TreeIterator`s have a one argument constructor `T(node)` which starts iteration from `node`.
