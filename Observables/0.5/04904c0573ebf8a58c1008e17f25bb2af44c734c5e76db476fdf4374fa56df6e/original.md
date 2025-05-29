```
onany(f, args...; weak::Bool = false, priority::Int = 0, update::Bool = false)
```

Calls `f` on updates to any observable refs in `args`. `args` may contain any number of `Observable` objects. `f` will be passed the values contained in the refs as the respective argument. All other objects in `args` are passed as-is.

See also: [`on`](@ref).
