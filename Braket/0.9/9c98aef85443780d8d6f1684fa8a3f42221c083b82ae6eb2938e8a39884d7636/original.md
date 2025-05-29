```
Probability(c::Circuit, targets) -> Circuit
Probability(c::Circuit) -> Circuit
```

Constructs a `Probability` measurement on qubits `targets` and adds it as a result to [`Circuit`](@ref) `c`.

`targets` may be one of:

  * A [`QubitSet`](@ref)
  * A `Vector` of `Int`s and/or [`Qubit`](@ref)s
  * An `Int` or `Qubit`
  * Absent, in which case the measurement will be applied to all qubits of `c`.

# Examples

```jldoctest
julia> c = Circuit();

julia> c = H(c, collect(0:3));

julia> c = Probability(c, 2);
```
