```
basis([IntType], nbits::Int) -> UnitRange{IntType}
basis([IntType], state::AbstractArray) -> UnitRange{IntType}
```

Returns the UnitRange for basis in Hilbert Space of nbits qubits. If an array is supplied, it will return a basis having the same size with the first diemension of array.
