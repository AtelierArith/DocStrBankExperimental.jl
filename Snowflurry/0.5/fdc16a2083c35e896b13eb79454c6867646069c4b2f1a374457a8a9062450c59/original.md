```
CircuitContainsAReadoutTranspiler
```

A transpiler stage which ensures that at least one `Readout` instruction is present in the `QuantumCircuit`. Otherwise, an error is thrown. This transpiler stage leaves the `QuantumCircuit` unchanged.

# Examples

```jldoctest
julia> transpiler = CircuitContainsAReadoutTranspiler();

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
               

julia> circuit = QuantumCircuit(qubit_count=2, instructions = [hadamard(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H──
          
q[2]:─────
          

julia> transpiled_circuit = transpile(transpiler, circuit)
ERROR: ArgumentError: QuantumCircuit is missing a `Readout`. Would not return any result.
[...]
```
