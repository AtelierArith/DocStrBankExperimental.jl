```
abstract type PipeMode <: TransmissionMode
```

`TransmissionMode` mode for additional variable potential.

`PipeMode`s are by default unidirectional. If you plan to include bidirectional pipelines, you have to provide a new method to the function [`is_bidirectional`](@ref).
