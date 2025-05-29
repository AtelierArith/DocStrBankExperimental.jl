```
ReadoutsAreFinalInstructionsTranspiler
```

Transpiler stage which ensures that each `Readout` instruction is the last operation  on each qubit where readouts are present. It also verifies that repeated readouts  on the same qubit do not occur. An error is thrown if these verifications fail.  This transpiler stage leaves the `QuantumCircuit` unchanged.

# Examples

```jldoctest
julia> transpiler = ReadoutsAreFinalInstructionsTranspiler();

julia> circuit = QuantumCircuit(qubit_count=2, instructions = [hadamard(1), readout(1,1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H────✲──
               
q[2]:──────────
               

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H────✲──
               
q[2]:──────────
               

julia> circuit = QuantumCircuit(
                    qubit_count=2,
                    instructions = [hadamard(1), readout(1,1), sigma_x(1)]
                )
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H────✲────X──
                    
q[2]:───────────────
                    

julia> transpiled_circuit = transpile(transpiler, circuit)
ERROR: AssertionError: Cannot perform `Gate` following `Readout` on qubit: 1
[...]

julia> circuit = QuantumCircuit(qubit_count=2, instructions = [readout(1,1), readout(1,2)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──✲────✲──
               
q[2]:──────────
               

julia> transpiled_circuit = transpile(transpiler, circuit)
ERROR: AssertionError: Found multiple `Readouts` on qubit: 1
[...]
```
