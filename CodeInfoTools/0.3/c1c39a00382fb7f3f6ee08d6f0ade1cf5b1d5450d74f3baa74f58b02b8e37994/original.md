```
finish(b::Builder)
```

Create a new `CodeInfo` instance from a [`Builder`](@ref). Renumbers the wrapped [`Canvas`](@ref) in-place – then copies information from the original `CodeInfo` instance and inserts modifications from the wrapped [`Canvas`](@ref)
