```
update_circuit_qubit_count(
    quantum_cicuit::QuantumCircuit,
    qubit_count::Int,
)::QuantumCircuit
```

Updates the `qubit_count` of the `quantum_circuit`.

# Examples

```jldoctest
julia> circuit = QuantumCircuit(qubit_count = 1, instructions = [sigma_x(1)])
Quantum Circuit Object:
   qubit_count: 1 
   bit_count: 1 
q[1]:──X──
          



julia> larger_circuit = update_circuit_qubit_count(circuit, 2)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 1 
q[1]:──X──
          
q[2]:─────
          


```
