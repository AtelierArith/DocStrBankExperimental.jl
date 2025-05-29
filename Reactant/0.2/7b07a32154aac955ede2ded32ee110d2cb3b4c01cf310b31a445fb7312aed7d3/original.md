```
with_config(f; kwargs...)
```

Run the function `f` within a dynamic scope such that all uses of the config within this scope will use the provided values.

# Extended Help

## Configuration Options

### Lowering

  * `lower_partialsort_to_approx_top_k`: Whether to lower `partialsort` and `partialsortperm` to `Ops.approx_top_k`. Note that XLA only supports lowering `ApproxTopK` for TPUs unless `fallback_approx_top_k_lowering` is set to `true`.
  * `fallback_approx_top_k_lowering`: Whether to lower `Ops.approx_top_k` to `stablehlo.top_k` if the XLA backend doesn't support `ApproxTopK`. Defaults to `true`.

### DotGeneral

  * `dot_general_algorithm`: Algorithm preset for `stablehlo.dot_general`. Can be `nothing`, [`DotGeneralAlgorithm`](@ref) or [`DotGeneralAlgorithmPreset`](@ref). Defaults to `DotGeneralAlgorithmPreset.DEFAULT`.
  * `dot_general_precision`: Precision for `stablehlo.dot_general`. Can be `nothing`, or [`PrecisionConfig`](@ref). Defaults to `PrecisionConfig.DEFAULT`.
  * `convolution_precision`: Precision for `stablehlo.convolution`. Can be `nothing`, or [`PrecisionConfig`](@ref). Defaults to `PrecisionConfig.DEFAULT`.
