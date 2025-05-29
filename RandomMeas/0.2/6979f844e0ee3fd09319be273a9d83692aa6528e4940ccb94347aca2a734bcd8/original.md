```
import_MeasurementGroup(filepath::String; predefined_settings=nothing, site_indices=nothing) -> MeasurementGroup
```

Import a MeasurementGroup object from an NPZ file.

# Arguments

  * `filepath::String`: The path to the NPZ file containing the exported MeasurementGroup data.
  * `predefined_settings` (optional): A vector of predefined measurement settings (one per MeasurementData object). If provided, its length must equal the exported NU.
  * `site_indices` (optional): A vector of N site indices to use when reconstructing the measurement setting. If not provided, default site indices are generated using `siteinds("Qubit", N)`.

# Returns

A MeasurementGroup object with:

  * Measurement results reconstructed from a 3D array of shape (NU, NM, N).
  * A measurement setting for each MeasurementData object reconstructed from a 4D array of shape (NU, N, 2, 2) if present, or taken from `predefined_settings` if provided.
