```
SubtreeIterator(t::AbstractRootedTree)
```

Lazy iterator representation of the [`subtrees`](@ref) of the rooted tree `t`. Similar to [`RootedTreeIterator`](@ref), you should `copy` the iterates if you want to store or modify them during the iteration since they may be views to internal caches.
