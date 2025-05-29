```
export_measurement_data(data::MeasurementData, filepath::String)
```

Exports measurement data to a `.npz` file.

# Arguments

  * `data::MeasurementData`: The measurement data object containing measurement results and optionally a LocalUnitaryMeasurementSetting setting.
  * `filepath::String`: The file path where the data will be exported.

# Details

  * The `measurement_results` are exported directly as they are.
  * If `measurement_setting` is provided, the associated `local_unitaries` are extracted, reshaped, and included in the export.

# Notes

  * The exported `.npz` file will contain:

      * `"measurement_results"`: A 2D array of shape `(NM, N)`, where:

          * `NM`: Number of measurements per setting.
          * `N`: Number of qubits/sites.
      * `"local_unitaries"` (optional): A 4D array of shape `(N, 2, 2)` representing the unitary transformations for each site.

# Example

```julia

# Create MeasurementData object
data = MeasurementData(measurement_results; measurement_setting=measurement_setting)

# Export to a file
export_measurement_data(data, "exported_data.npz")
```
