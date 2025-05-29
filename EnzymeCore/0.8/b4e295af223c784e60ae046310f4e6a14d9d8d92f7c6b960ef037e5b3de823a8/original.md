```
struct ReverseModeSplit{
    ReturnPrimal,
    ReturnShadow,
    Width,
    RuntimeActivity,
    ModifiedBetween,
    ABI,
    ErrFuncIfWritten
} <: Mode{ABI,ErrIfFuncWritten,RuntimeActivity}
    WithPrimal(::Enzyme.Mode)
```

Subtype of [`Mode`](@ref) for split reverse mode differentiation, to use in [`autodiff_thunk`](@ref) and variants.

# Type parameters

  * `ReturnShadow`: whether to return the shadow return value from the augmented-forward.
  * `Width`: batch size (pick `0` to derive it automatically)
  * `ModifiedBetween`: `Tuple` of each argument's "modified between" state (pick `true` to derive it automatically).
  * other parameters: see [`ReverseMode`](@ref)

!!! warning
    The type parameters of `ReverseModeSplit` are not part of the public API and can change without notice. Please use one of the following concrete instantiations instead: 

      * [`ReverseSplitNoPrimal`](@ref)
      * [`ReverseSplitWithPrimal`](@ref)

    You can modify them with the following helper functions:

      * [`WithPrimal`](@ref) / [`NoPrimal`](@ref)
      * [`set_err_if_func_written`](@ref) / [`clear_err_if_func_written`](@ref)
      * [`set_runtime_activity`](@ref) / [`clear_runtime_activity`](@ref)
      * [`set_abi`](@ref)
      * [`ReverseSplitModified`](@ref), [`ReverseSplitWidth`](@ref)

