```
MaintainInputs <: MeasurementModel
```

Carry over a subset of the input variables to the next step in a calculation.  Typically used in consort with a `ParallelMeasurementModel` when inputs to this step will also be required in subsequent steps.
