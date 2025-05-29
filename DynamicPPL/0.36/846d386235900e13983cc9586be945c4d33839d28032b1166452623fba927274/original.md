```
VarInfo([rng, ]model[, sampler, context])
```

Generate a `VarInfo` object for the given `model`, by evaluating it once using the given `rng`, `sampler`, and `context`.

!!! warning
    This function currently returns a `VarInfo` with its metadata field set to a `NamedTuple` of `Metadata`. This is an implementation detail. In general, this function may return any kind of object that satisfies the `AbstractVarInfo` interface. If you require precise control over the type of `VarInfo` returned, use the internal functions `untyped_varinfo`, `typed_varinfo`, `untyped_vector_varinfo`, or `typed_vector_varinfo` instead.

