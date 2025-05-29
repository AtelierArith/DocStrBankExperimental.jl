```
SlabBuffer{SlabSize}(;finalize::Bool = true)
```

Create a slab allocator whose slabs are of size `SlabSize`. If you set the `finalize` keyword argument to `false`, then you will need to explicitly call `Bumper.free()` when you are done with a `SlabBuffer`. This is not recommended.
