```
get_name(circuit::QuantumCircuit)::String
```

Returns the name of the `circuit` and the corresponding job.

# Examples

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2, name = "my_circuit");

julia> get_name(c)
"my_circuit"

```
