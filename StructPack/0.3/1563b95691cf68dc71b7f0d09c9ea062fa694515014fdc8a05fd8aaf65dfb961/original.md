```
typeparamformats(T::Type [, ctx::Context])
```

Return the formats of the type parameters of `T` when packing / unpacking under `ctx`.

Defaults to `DefaultFormat()` for each type parameter.

This method is consulted when packing / unpacking types via [`TypeFormat`](@ref) and [`TypedFormat`](@ref).
