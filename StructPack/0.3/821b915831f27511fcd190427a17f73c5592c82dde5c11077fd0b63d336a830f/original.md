```
fieldnames(T::Type [, ctx::Context])
```

Return the field names of `T` when packing / unpacking in [`AbstractStructFormat`](@ref) under `ctx`.

Defaults to `Base.fieldnames(T)`.
