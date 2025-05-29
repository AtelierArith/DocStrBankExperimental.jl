```
twist(tsrc::AbstractTensorMap, i::Int; inv::Bool=false) -> tdst
twist(tsrc::AbstractTensorMap, is; inv::Bool=false) -> tdst
```

Apply a twist to the `i`th index of `tsrc` and return the result as a new tensor. If `inv=true`, use the inverse twist.

See [`twist!`](@ref) for storing the result in place.
