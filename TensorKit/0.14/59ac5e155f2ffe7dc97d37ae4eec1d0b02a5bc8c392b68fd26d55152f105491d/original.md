```
twist!(t::AbstractTensorMap, i::Int; inv::Bool=false) -> t
twist!(t::AbstractTensorMap, is; inv::Bool=false) -> t
```

Apply a twist to the `i`th index of `t`, or all indices in `is`, storing the result in `t`. If `inv=true`, use the inverse twist.

See [`twist`](@ref) for creating a new tensor.
