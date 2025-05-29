```
get_overlap(
    data_1::MeasurementData,
    data_2::MeasurementData
)
```

Compute the overlap between two quantum states for a single measurement setting.

# Arguments

  * `data_1::MeasurementData`: Measurement Data for the first state, with dimensions `(NM, N)`.
  * `data_2::MeasurementData`: Measurement Data for the second state, with dimensions `(NM, N)`.

# Returns

  * The computed overlap for the single measurement setting.
