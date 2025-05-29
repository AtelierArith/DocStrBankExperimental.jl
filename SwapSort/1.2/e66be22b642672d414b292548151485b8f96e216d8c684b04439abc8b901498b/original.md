```
tuplesort(t::Tuple; lt=isless, by=identity)
```

Return a sorted tuple. `lt` and `by` keywords work the same as `Base.sort`. `tuplesort` calls [`swapsort`](@ref) and supports at most 64 elements.
