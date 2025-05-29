```
swapsort(a...; lt=isless, by=identity)
```

Sort the arguments, returning a sorted tuple. `lt` and `by` keywords work the same as `Base.sort`. `swapsort` supports up to 64 arguments. See also [`tuplesort`](@ref).
