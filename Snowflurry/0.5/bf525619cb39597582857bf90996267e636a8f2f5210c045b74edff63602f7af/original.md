```
SequentialTranspiler(Vector{<:Transpiler})
```

Composite transpiler object which is constructed from an array  of `Transpiler` stages. Calling      `transpile(::SequentialTranspiler,::QuantumCircuit)` will apply each stage in sequence to the input circuit and return a transpiled output circuit. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Examples

```jldoctest
julia> transpiler = SequentialTranspiler([
                        CompressSingleQubitGatesTranspiler(),
                        CastToPhaseShiftAndHalfRotationXTranspiler()
                    ]);

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [sigma_x(1), hadamard(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X────H──
               
q[2]:──────────
               



julia> transpile(transpiler,circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Z────X_90────Z_90────X_m90────Z──
                                                              
q[2]:───────────────────────────────────
                                                              



julia> circuit = QuantumCircuit(
                    qubit_count = 3,
                    instructions = [
                        sigma_x(1),
                        sigma_y(1),
                        control_x(2,3),
                        phase_shift(1,π/3)
                    ])
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X────Y─────────P(1.0472)──

q[2]:────────────*───────────────
                 |               
q[3]:────────────X───────────────
                                 



julia> transpile(transpiler,circuit)
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──P(-2.0944)───────
                        
q[2]:────────────────*──
                     |  
q[3]:────────────────X──
                        



```
