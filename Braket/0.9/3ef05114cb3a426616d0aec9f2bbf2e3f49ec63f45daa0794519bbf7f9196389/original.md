```
Braket.Expectation(o, targets) -> Braket.Expectation
Braket.Expectation(o) -> Braket.Expectation
```

Constructs a Braket.Expectation of an observable `o` on qubits `targets`.

`o` may be one of:

  * Any [`Observable`](@ref Braket.Observables.Observable)
  * A `String` corresponding to an `Observable` (e.g. `"x"``)
  * A `Vector{String}` in which each element corresponds to an `Observable`

`targets` may be one of:

  * A [`QubitSet`](@ref)
  * A `Vector` of `Int`s and/or [`Qubit`](@ref)s
  * An `Int` or `Qubit`
  * Absent, in which case the observable `o` will be applied to all qubits provided it is a single qubit observable.
