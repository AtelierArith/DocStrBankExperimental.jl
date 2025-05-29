```
fieldtypes(T::Type [, ctx::Context])
```

Return the field types of `T` when packing / unpacking in [`AbstractStructFormat`](@ref) under `ctx`.

Defaults to `Base.fieldtypes(T)`.
