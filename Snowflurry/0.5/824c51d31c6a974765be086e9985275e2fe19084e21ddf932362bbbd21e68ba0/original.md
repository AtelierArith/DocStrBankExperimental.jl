```
get_quantum_circuit(pauli::PauliGroupElement)::QuantumCircuit
```

Returns the Pauli gates of a `PauliGroupElement` as a [`QuantumCircuit`](@ref).

# Examples

```jldoctest
julia> circuit = QuantumCircuit(qubit_count = 2);

julia> push!(circuit, sigma_x(1), sigma_y(2))
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X───────
               
q[2]:───────Y──
               



julia> pauli = get_pauli(circuit, imaginary_exponent = 1, negative_exponent = 1)
Pauli Group Element:
-1.0im*X(1)*Y(2)



julia> get_quantum_circuit(pauli)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X───────
               
q[2]:───────Y──
               



```
