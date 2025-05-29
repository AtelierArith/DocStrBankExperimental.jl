```
export_MeasurementGroup(group::MeasurementGroup{T}, filepath::String)
```

Export a MeasurementGroup object to an NPZ file.

# Arguments

  * `group::MeasurementGroup{T}`: A MeasurementGroup object where each MeasurementData may have its own measurement setting of type T (with T <: Union{Nothing, LocalUnitaryMeasurementSetting, ComputationalBasisMeasurementSetting}).
  * `filepath::String`: The file path where the NPZ file will be written.

# Details

  * The measurement results from each MeasurementData object (each of shape (NM, N)) are stacked into a 3D array of shape (NU, NM, N), where NU is the number of MeasurementData objects.
  * The measurement settings are exported as a Complex array of size NU x N x 2 x 2 if present.
