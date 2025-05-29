```
qubits(c::Circuit) -> QubitSet
```

Returns a [`QubitSet`](@ref) containing all qubits that `c` is defined on.

# Examples

```jldoctest
julia> c = Circuit();

julia> H(c, 0);

julia> CNot(c, 0, 1);

julia> qubits(c)
QubitSet with 2 elements:
  0
  1
```
