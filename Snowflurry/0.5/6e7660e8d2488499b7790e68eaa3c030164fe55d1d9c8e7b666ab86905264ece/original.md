```
permute_qubits!(
    circuit::QuantumCircuit,
    qubit_mapping::AbstractDict{T,T}
) where T<:Integer
```

Modifies a `circuit` by moving the gates to other qubits based on a `qubit_mapping`.

The dictionary `qubit_mapping` contains key-value pairs describing how to update the target qubits. The key indicates which target qubit to change while the associated value specifies the new qubit. All the keys in the dictionary must be present as values and vice versa.

For instance, `Dict(1 => 2)` is not a valid `qubit_mapping`, but `Dict(1 => 2, 2 => 1)` is valid.

# Examples

```jldoctest
julia> c = QuantumCircuit(qubit_count = 3);

julia> push!(c, sigma_x(1), hadamard(2), sigma_y(3))
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X────────────
                    
q[2]:───────H───────
                    
q[3]:────────────Y──                    



julia> permute_qubits!(c, Dict(1 => 3, 3 => 1))

julia> show(c)
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:────────────Y──
                    
q[2]:───────H───────
                    
q[3]:──X────────────
                    


```
