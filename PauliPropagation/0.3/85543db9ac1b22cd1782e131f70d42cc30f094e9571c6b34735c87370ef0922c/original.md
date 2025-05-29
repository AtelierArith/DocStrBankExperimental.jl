```
transposecliffordmap(map_array::Vector{Tuple{UInt8,Int}})
```

Transpose the Clifford gate `maparray` so that the output map is the inverse of the input map. For example, `transposecliffordmap(clifford_map[:H])` returns the map for the inverse of the Hadamard gate, which is the same map.
