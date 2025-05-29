```
AbstractDimStack
```

Abstract supertype for dimensional stacks.

These have multiple layers of data, but share dimensions.

Notably, their behaviour lies somewhere between a `DimArray` and a `NamedTuple`:

  * indexing with a `Symbol` as in `dimstack[:symbol]` returns a `DimArray` layer.
  * iteration and `map` apply over array layers, as indexed with a `Symbol`.
  * `getindex` and many base methods are applied as for `DimArray` - to avoid the need to always use `map`.

This design gives very succinct code when working with many-layered, mixed-dimension objects. But it may be jarring initially - the most surprising outcome is that `dimstack[1]` will return a `NamedTuple` of values for the first index in all layers, while `first(dimstack)` will return the first value of the iterator - the `DimArray` for the first layer.

See [`DimStack`](@ref) for the concrete implementation. Most methods are defined on the abstract type.

To extend `AbstractDimStack`, implement argument and keyword version of [`rebuild`](@ref) and also [`rebuild_from_arrays`](@ref).

The constructor of an `AbstractDimStack` must accept a `NamedTuple`.
