```
MultipleCalibration{A, N, T <: Table} <: AbstractCalibration{A, N}
```

A mutable type holding all data and settings for a calibration curve. `A` determines analyte type, and `N` determines numeric type. Only `Float64` is supported because of issue of `GLM`.

# Fields

  * `analyte`: `Tuple{A, Any}`. First element is the analyte being quantified, and the second element is its internal standard for which `nothing` indicates no internal standard.
  * `type`: `Bool` determines whether fitting a linear line (`true`) or quadratic curve (`false`).
  * `zero`: `Bool` determines whether forcing the curve crossing (0, 0) (`true`) or ignoring it (`false`).
  * `weight`: `Float64` represents the exponential applying to each element of `x` as a weighting vector.
  * `formula`: `FormulaTerm`, the formula for fitting calibration curve.
  * `table`: `TypedTable.Table`, the cleaned up calibration data, containing 7 columns.

      * `id`: Point name
      * `level`: The index of concentration level. The larger, the higher concentraion it represents.
      * `y`: Signal or relative signal
      * `x`: True concentraion
      * `x̂`: Predicted concentration
      * `accuracy`: Accuracy, i.e. `x̂/x`.
      * `include`: Whether this point is included or not
  * `model`: `GLM` object.
