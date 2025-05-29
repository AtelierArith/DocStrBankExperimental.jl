```
valueformat(T::Type, state, fmt::Format [, ctx::Context])::Format
```

Return the format of the value at iteration state `state` when saving the entries of `T` in format `fmt`.

This method is used when packing or unpacking values in [`AbstractVectorFormat`](@ref) and [`AbstractMapFormat`](@ref).
