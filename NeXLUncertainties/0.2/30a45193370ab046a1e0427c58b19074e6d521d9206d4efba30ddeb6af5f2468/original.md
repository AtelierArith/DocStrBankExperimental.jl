```
ParallelMeasurementModel <: MeasurementModel
```

A `ParallelMeasurementModel` is a collection of `MeasurementModel`s that can be executed simultaneously since they share the same inputs (or a subset of the same inputs). `ParallelMeasurementModel`s should be favored over `ComposedMeasurementModel`s since they can be threaded and combining Jacobians is more computationally efficient.

```
ParallelMeasurementModel(models::AbstractVector{MeasurementModel}, multithread=false)
```

While `ParallelMeasurementModel` supports multi-threading, multi-threading should be used only when the cost of the calculation is going to exceed the overhead necessary to create and manage the thread.  Usually this means, only use `multithread=true` on one of the outer-most steps of a large calculation where splitting the calculation can keep the Jacobians as small as possible until the last possible moment.

The result of the ParallelMeasurementModel is the union of the outputs from each model.
