```
keytype(T::Type, state, fmt::Format [, ctx::Context])::Type
```

Return the type of the key at iteration state `state` when saving the entries of `T` in format `fmt`.

This method is called when unpacking values in [`AbstractMapFormat`](@ref).
