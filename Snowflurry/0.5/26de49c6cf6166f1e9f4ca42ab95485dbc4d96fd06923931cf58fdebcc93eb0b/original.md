```
get_num_qubits(circuit::QuantumCircuit)::Int
```

Returns the number of qubits in a `circuit`.

# Examples

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2);

julia> get_num_qubits(c)
2

```
