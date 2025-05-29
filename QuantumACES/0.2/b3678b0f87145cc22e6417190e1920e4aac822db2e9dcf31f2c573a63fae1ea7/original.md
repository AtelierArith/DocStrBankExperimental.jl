```
make_layer(gate_type::String, range_set::Vector{Vector{Int}}, n::Integer; index::Integer = 0)
```

Returns a layer of `gate_type` gates, each acting on the qubits in `range_set`, where the layer acts on `n` qubits, optionally specifying the gate index `index`.
