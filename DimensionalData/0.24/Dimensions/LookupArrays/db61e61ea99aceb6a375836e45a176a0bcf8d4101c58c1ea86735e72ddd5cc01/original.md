```
NoMetadata <: AbstractMetadata

NoMetadata()
```

Indicates an object has no metadata. But unlike using `nothing`,  `get`, `keys` and `haskey` will still work on it, `get` always returning the fallback argument. `keys` returns `()` while `haskey` always returns `false`.
