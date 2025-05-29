```
Batch{A, M <: AnalysisMethod{A}, C <: AbstractVector{<: AbstractCalibration{<: A}}, D <: Union{AnalysisTable{<: A}, Nothing}}
```

A type representing a batch for quantitative analysis. `A` determines analyte type, and `T` determines table type.

# Fields

  * `method`: `M`, method.
  * `calibration`: `C`, calibration curves.
  * `data`: `D`, data for analysis, .

# Properties

  * `analyte`: `AbstractVector{A}`, analytes in user-defined types, identical to `method.analyte`.
  * `isd`: `AbstractVector{<: A}`, analytes which are internal standards, identical to `method.isd`.
  * `nonisd`: `AbstractVector{<: A}`, analytes which are not internal standards, identical to `method.nonisd`.
  * `point`: `AbstractVector` or `Nothing`, calibration points, identical to `method.point`.
  * `level`: `AbstractVector{Int}`, calibration levels, identical to `method.level`.

# Constructors

  * `Batch(method, calibration, data = nothing)`
