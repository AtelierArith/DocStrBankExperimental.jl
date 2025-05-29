```
import_measurement_data(filepath::String; predefined_setting=nothing, site_indices=nothing)
```

Imports measurement results and optional measurement settings from an archive file.

# Arguments

  * `filepath::String`: Path to the `.npz` file containing the measurement results and optionally local unitaries. The file should contain at least a field `measurement_results` (2D binary array of shape `(NM, N)`), and optionally a field `local_unitaries` (local unitaries as a Nx2x2 array).
  * `predefined_setting` (optional): A predefined `MeasurementSetting` object. If provided, this will be used instead of the file's setting.
  * `site_indices` (optional): A vector of site indices to be used when constructing `LocalUnitaryMeasurementSetting` from the field `local_unitaries` (only relevant if predefined_setting is not provided). If not provided, the default site indices will be generated internally.

# Returns

A `MeasurementData` object containing the imported results and settings.

# Examples

```julia
# Import with predefined settings
setting = LocalUnitaryMeasurementSetting(local_unitaries; site_indices=siteinds("Qubit", 5))
data_with_setting = import_measurement_data("data.npz"; predefined_setting=setting)

# Import with site indices provided
data_with_indices = import_measurement_data("data.npz"; site_indices=siteinds("Qubit", 5))

# Import without any additional options
data = import_measurement_data("data.npz")
```
