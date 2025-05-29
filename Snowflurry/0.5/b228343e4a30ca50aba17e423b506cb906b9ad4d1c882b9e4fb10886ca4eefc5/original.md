```
get_num_bits(circuit::QuantumCircuit)::Int
```

Returns the number of classical bits in a `circuit`.

# Examples

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2, bit_count=3);

julia> get_num_bits(c)
3

```
