```
calibration(anisd::Tuple, tbl::Table; analyte = 1, isd = 0, type = true, zero = false, weight = 0)
calibration(batch::Batch{A}, ana::B; id = sample(batch.method.signaltable), isd = isdof(batch.method, analyte),
                    type = true, zero = false, weight = 0) where {A, B <: A}
calibration(method::AnalysisMethod{A}, ana::B; id = sample(method.signaltable), isd = isdof(method, analyte),
            type = true, zero = false, weight = 0) where {A, B <: A}
```

Create `MultipleCalibration`.

  * `anisd`: `Tuple{B <: A, Any}` which will be stored as `analyte`. The first element is the analyte to be quantified, and the second element is its internal standard, which `nothing` means no internal standard.
  * `analyte`: `B` which will be stored as first argument of `analyte`.
  * `tbl`: `TypedTable.Table` which will be stored as `table`. It is clean-up calibration data for points selection.
  * `method`: `AnalysisMethod`, calibration method and data.
  * `batch`: `Batch`.

# Keyword arguments

  * `type`: `Bool` determines whether fitting a linear line (`true`) or quadratic curve (`false`), which will be stored as `type`.
  * `zero`: `Bool` determines whether forcing the curve crossing (0, 0) (`true`) or ignoring it (`false`), which will be stored as `zero`.
  * `weight`: `Float64` represents the exponential applying to each element of `x` as a weighting vector, which will be stored as `weight`.
