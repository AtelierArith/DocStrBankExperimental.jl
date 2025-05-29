```
AnalysisMethod{A, M <: Table, C <: AbstractDataTable, D <: Union{AbstractDataTable, Nothing}}
```

A type containing analytes settings, and source calibration data. `A` determines analyte type.

# Fields

  * `analytetable`: `M` contaning three columns.

      * `analyte`: `AbstractVector{A}`, analytes in user-defined types.
      * `isd`: `AbstractVector{Int}`, index of internal standard. `0` means no internal standard, and `-1` means the analyte itself is a internal standard.
      * `calibration`: index of analyte for calibration curve. `-1` means the analyte itself is a internal standard, so it will not be put into any calibration curve.
  * `signal`: `Symbol`, type and key name of experimental acquisition data, e.g. `:area`.
  * `rel_sig`: `Symbol`, key name of relative signal.
  * `est_conc`: `Symbol`, key name of estimated concentration.
  * `true_conc`: `Symbol`, key name of true concentration.
  * `acc`: `Symbol`, key name of accuracy.
  * `pointlevel`: `Vector{Int}` matching each point to level. It can be empty if there is only one level in `conctable`.
  * `conctable`: `C <: AbstractDataTable{<: A, Int}` containing concentration data for each level. Samples must integers. One level indicates using `SingleCalibration`.
  * `signaltable`: `D <: AbstractDataTable{A}` containig signal for each point. It can be `nothing` if signal data is unecessary.

# Properties

  * `analyte`: `AbstractVector{A}`, analytes in user-defined types, identical to `analytetable.analyte`.
  * `isd`: `AbstractVector{A}`, analytes which are internal standards.
  * `nonisd`: `AbstractVector{A}`, analytes which are not internal standards.
  * `point`: `AbstractVector{S}`, calibration points, identical to `sampleobj(signaltable)`. If `signaltable` is `nothing`, this value is `nothing` too.
  * `level`: `AbstractVector{Int}`, calibration levels, identical to `sampleobj(conctable)`.
