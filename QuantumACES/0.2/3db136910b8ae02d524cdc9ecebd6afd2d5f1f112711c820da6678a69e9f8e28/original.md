```
make_layer(gate_type::String, range::Vector{Int}, n::Integer; index::Integer = 0)
```

Returns a layer of single-qubit `gate_type` gates acting on the qubits in `range`, where the layer acts on `n` qubits, optionally specifying the gate index `index`.
