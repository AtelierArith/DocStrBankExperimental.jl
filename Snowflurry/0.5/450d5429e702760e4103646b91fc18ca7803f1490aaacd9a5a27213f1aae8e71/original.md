```
ReadoutsDoNotConflictTranspiler
```

Transpiler stage which ensures that each `Readout` instruction present in the `QuantumCircuit` does not have conflicting destination bits, Otherwise, an error is thrown.  This transpiler stage leaves the `QuantumCircuit` unchanged.

# Examples

```jldoctest
julia> transpiler = ReadoutsDoNotConflictTranspiler();

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
               

julia> circuit = QuantumCircuit(qubit_count=2, instructions = [readout(1,1), readout(2,1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──✲───────
               
q[2]:───────✲──
               

julia> transpiled_circuit = transpile(transpiler, circuit)
ERROR: ArgumentError: `Readouts` in `QuantumCircuit` have conflicting destination bit: 1
[...]
```
