```
typeparamtypes(T::Type [, ctx::Context])
```

Return the types of the type parameters of `T` when packing / unpacking under `ctx`.

!!! note
    If `T` has type parameters, this method **must** be implemented for packing / unpacking types via [`TypeFormat`](@ref) and their values via [`TypedFormat`](@ref).

