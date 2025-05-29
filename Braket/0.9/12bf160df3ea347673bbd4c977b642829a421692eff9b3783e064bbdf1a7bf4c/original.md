```
Braket.Expectation(c::Circuit, o, targets) -> Circuit
Braket.Expectation(c::Circuit, o) -> Circuit
```

Constructs a `Braket.Expectation` of an observable `o` on qubits `targets` and adds it as a result to [`Circuit`](@ref) `c`.

`o` may be one of:

  * Any [`Observable`](@ref Braket.Observables.Observable)
  * A `String` corresponding to an `Observable` (e.g. "x")
  * A `Vector{String}` in which each element corresponds to an `Observable`

`targets` may be one of:

  * A [`QubitSet`](@ref)
  * A `Vector` of `Int`s and/or [`Qubit`](@ref)s
  * An `Int` or `Qubit`
  * Absent, in which case the observable `o` will be applied to all qubits provided it is a single qubit observable.

# Examples

```jldoctest
julia> c = Circuit();

julia> c = H(c, collect(0:10));

julia> c = Braket.Expectation(c, Braket.Observables.Z(), 0);

julia> c = Braket.Expectation(c, Braket.Observables.X());
```
