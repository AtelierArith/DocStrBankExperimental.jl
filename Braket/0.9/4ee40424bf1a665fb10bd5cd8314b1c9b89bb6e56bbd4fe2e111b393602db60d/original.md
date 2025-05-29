```
Braket.DensityMatrix(targets) -> Braket.DensityMatrix
Braket.DensityMatrix() -> Braket.DensityMatrix
```

Constructs a Braket.DensityMatrix on qubits `targets`.

`targets` may be one of:

  * A [`QubitSet`](@ref)
  * A `Vector` of `Int`s and/or [`Qubit`](@ref)s
  * An `Int` or `Qubit`
  * Absent, in which case the measurement will be applied to all qubits.
