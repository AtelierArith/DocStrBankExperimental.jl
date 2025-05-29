```
make_layer(gate_types::Vector{String}, ranges::Vector{Vector{Int}}, n::Integer; index::Integer = 0)
```

Returns a layer of single-qubit gates, with gate types specified by `gate_types` and the qubits upon which they act specified by `ranges`, where the layer acts on `n` qubits, optionally specifying the gate index `index`.
