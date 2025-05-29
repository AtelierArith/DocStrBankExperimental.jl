```
size_global(x::PencilArray, [order = LogicalOrder()])
size_global(x::PencilArrayCollection, [order = LogicalOrder()])
```

Global dimensions associated to the given array.

By default, the logical dimensions of the dataset are returned.

If `order = LogicalOrder()`, this is the same as `size(x)`.

See also [`size_global(::Pencil)`](@ref).
