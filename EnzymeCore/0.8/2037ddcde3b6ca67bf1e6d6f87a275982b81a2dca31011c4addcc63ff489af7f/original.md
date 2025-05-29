```
abstract type Mode{ABI,ErrIfFuncWritten,RuntimeActivity}
```

Abstract type for which differentiation mode will be used.

# Subtypes

  * [`ForwardMode`](@ref)
  * [`ReverseMode`](@ref)
  * [`ReverseModeSplit`](@ref)

# Type parameters

  * `ABI`: what runtime [`ABI`](@ref) to use
  * `ErrIfFuncWritten`: whether to error when the function differentiated is a closure and written to.
  * `RuntimeActivity`: whether to enable runtime activity (default off)

!!! warning
    The type parameters of `Mode` are not part of the public API and can change without notice. You can modify them with the following helper functions:

      * [`WithPrimal`](@ref) / [`NoPrimal`](@ref)
      * [`set_err_if_func_written`](@ref) / [`clear_err_if_func_written`](@ref)
      * [`set_runtime_activity`](@ref) / [`clear_runtime_activity`](@ref)
      * [`set_abi`](@ref)

