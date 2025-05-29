```
struct ForwardMode{
    ReturnPrimal,
    ABI,
    ErrIfFuncWritten,
    RuntimeActivity
} <: Mode{ABI,ErrIfFuncWritten,RuntimeActivity}
```

Subtype of [`Mode`](@ref) for forward mode differentiation.

# Type parameters

  * `ReturnPrimal`: whether to return the primal return value from the augmented-forward.
  * other parameters: see [`Mode`](@ref)

!!! warning
    The type parameters of `ForwardMode` are not part of the public API and can change without notice. Please use one of the following concrete instantiations instead:

      * [`Forward`](@ref)
      * [`ForwardWithPrimal`](@ref)

    You can modify them with the following helper functions:

      * [`WithPrimal`](@ref) / [`NoPrimal`](@ref)
      * [`set_err_if_func_written`](@ref) / [`clear_err_if_func_written`](@ref)
      * [`set_runtime_activity`](@ref) / [`clear_runtime_activity`](@ref)
      * [`set_abi`](@ref)

