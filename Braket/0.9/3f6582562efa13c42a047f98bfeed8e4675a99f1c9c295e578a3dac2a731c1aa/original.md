```
qubit_count(c::Circuit) -> Int
```

Returns the number of qubits that `c` is defined on.

# Examples

```jldoctest
julia> c = Circuit();

julia> H(c, 0);

julia> CNot(c, 0, 1);

julia> qubit_count(c)
2
```
