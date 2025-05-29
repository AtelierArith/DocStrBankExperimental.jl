```
keyformat(T::Type, state, fmt::Format [, ctx::Context])::Format
```

Return the format of the key at iteration state `state` when saving the entries of `T` in format `fmt`.

This method is called when packing or unpacking values in [`AbstractMapFormat`](@ref).
