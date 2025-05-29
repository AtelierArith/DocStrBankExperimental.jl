```
DotGeneralAlgorithmPreset
```

Controls the `precision_config` for `stablehlo.dot_general`. Valid values are:

  * `DEFAULT`
  * `ANY_F8_ANY_F8_F32`
  * `ANY_F8_ANY_F8_F32_FAST_ACCUM`
  * `ANY_F8_ANY_F8_ANY`
  * `ANY_F8_ANY_F8_ANY_FAST_ACCUM`
  * `F16_F16_F16`
  * `F16_F16_F32`
  * `BF16_BF16_BF16`
  * `BF16_BF16_F32`
  * `BF16_BF16_F32_X3`
  * `BF16_BF16_F32_X6`
  * `BF16_BF16_F32_X9`
  * `F32_F32_F32`
  * `F64_F64_F64`

The following functions are available:

`supported_lhs_eltype(dot_algorithm_preset::DotGeneralAlgorithmPreset.T)`   `supported_rhs_eltype(dot_algorithm_preset::DotGeneralAlgorithmPreset.T)`   `accumulation_eltype(dot_algorithm_preset::DotGeneralAlgorithmPreset.T)`   `supported_output_eltype(dot_algorithm_preset::DotGeneralAlgorithmPreset.T, T1, T2)`   `MLIR.IR.Attribute(dot_algorithm_preset::DotGeneralAlgorithmPreset.T, T1, T2)`
