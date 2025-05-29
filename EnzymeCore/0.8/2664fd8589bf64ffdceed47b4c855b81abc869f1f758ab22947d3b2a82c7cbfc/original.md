```
struct ReverseMode{
    ReturnPrimal,
    RuntimeActivity,
    ABI,
    Holomorphic,
    ErrIfFuncWritten
} <: Mode{ABI,ErrIfFuncWritten,RuntimeActivity}
```

Subtype of [`Mode`](@ref) for reverse mode differentiation.

# Type parameters

  * `ReturnPrimal`: whether to return the primal return value from the augmented-forward pass.
  * `Holomorphic`: Whether the complex result function is holomorphic and we should compute `d/dz`
  * other parameters: see [`Mode`](@ref)

!!! warning
    The type parameters of `ReverseMode` are not part of the public API and can change without notice. Please use one of the following concrete instantiations instead:

      * [`Reverse`](@ref)
      * [`ReverseWithPrimal`](@ref)
      * [`ReverseHolomorphic`](@ref)
      * [`ReverseHolomorphicWithPrimal`](@ref)

    You can modify them with the following helper functions:

      * [`WithPrimal`](@ref) / [`NoPrimal`](@ref)
      * [`set_err_if_func_written`](@ref) / [`clear_err_if_func_written`](@ref)
      * [`set_runtime_activity`](@ref) / [`clear_runtime_activity`](@ref)
      * [`set_abi`](@ref)

