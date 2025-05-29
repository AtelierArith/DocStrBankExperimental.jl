```
simulate_shots(c::QuantumCircuit, shots_count::Int = 100)
```

Emulates a quantum computer by running a circuit for a given number of shots and returning measurement results, as prescribed by the `Readout` instructions present in the circuit.  The distribution of measured states depends on the coefficients of the resulting state Ket.

# Examples

```jldoctest simulate_shots; filter = r"00|11"
julia> c = QuantumCircuit(qubit_count = 2);

julia> push!(c, hadamard(1), control_x(1, 2), readout(1, 1), readout(2, 2))
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H────*────✲───────
            |            
q[2]:───────X─────────✲──


julia> simulate_shots(c, 99)
99-element Vector{String}:
 "11"
 "00"
 "11"
 "11"
 "11"
 "11"
 "11"
 "00"
 "00"
 "11"
 ⋮
 "00"
 "00"
 "11"
 "00"
 "00"
 "00"
 "00"
 "00"
 "00"
```
