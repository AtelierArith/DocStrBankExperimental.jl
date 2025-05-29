```
applyreduce(f, op, target::Union{TraitTarget, GI.AbstractTrait}, obj; threaded, init, kw...)
```

Apply function `f` to all objects with the `target` trait, and reduce the result with an `op` like `+`. 

The order and grouping of application of `op` is not guaranteed.

If `threaded==true` threads will be used over arrays and iterables,  feature collections and nested geometries.

`init` functions the same way as it does in base Julia functions like `reduce`.
