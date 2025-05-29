```
SingleCalibration{A, N} <: AbstractCalibration{A, N}
```

A mutable type holding all data for single point calibration.

# Fields

  * `analyte`: `Tuple{A}` is the analyte with known concentration (internal standard).
  * `conc`: `Float64`, concentration of analyte.
