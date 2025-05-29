```
valuetype(T::Type, fmt::Format, state [, ctx::Context])::Type
```

Return the type of the value at iteration state `state` when saving the entries of `T` in format `fmt`.

This method is used when unpacking values in [`AbstractVectorFormat`](@ref) and [`AbstractMapFormat`](@ref).
