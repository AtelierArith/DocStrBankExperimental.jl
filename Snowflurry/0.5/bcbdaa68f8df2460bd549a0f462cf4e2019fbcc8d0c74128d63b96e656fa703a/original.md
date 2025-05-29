```
CastRxToRzAndHalfRotationXTranspiler
```

Transpiler stage which finds `RotationX(θ)` gates in an input circuit and converts (casts)  them into a sequence of gates (`Z90`, `X90`, `PhaseShift(θ)`, `XM90`, and `ZM90`) in a new circuit. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Examples

```jldoctest
julia> transpiler=CastRxToRzAndHalfRotationXTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [rotation_x(1,π/8)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Rx(0.3927)──
                   
q[2]:──────────────
                   

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Z_90────X_90────P(0.3927)────X_m90────Z_m90──
                                                    
q[2]:───────────────────────────────────────────────
                                                    

julia> compare_circuits(circuit, transpiled_circuit)
true

```
