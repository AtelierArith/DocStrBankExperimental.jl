```
ComposedMeasurementModel <: MeasurementModel
```

A `ComposedMeasurementModel` is used when the output from step-i will be used in a subsequent step.  Favor `ParallelMeasurementModel` whenever a collection of `MeasurementModel`s share the same inputs (or subsets of the same inputs) since the `ParallelMeasurementModel`s can be run on multiple threads and the Jacobians can be concatenated rather than multiplied. `ParallelMeasurementModel`s and `ComposedMeasurementModel`s can be combined to produce efficient calculation models.

The final result of the ComposedMeasurementModel is the output of the final step.
