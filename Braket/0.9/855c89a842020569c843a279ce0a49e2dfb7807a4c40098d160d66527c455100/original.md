```
StateVector(c::Circuit) -> Circuit
```

Constructs a `StateVector` measurement on all qubits of `c` and adds it as a result to [`Circuit`](@ref) `c`.

# Examples

```jldoctest
julia> c = Circuit();

julia> c = H(c, collect(0:3));

julia> c = StateVector(c);
```
