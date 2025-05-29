```
RemoveSwapBySwappingGatesTranspiler
```

Transipler stage which removes the `Swap` gates from the `circuit` assuming all-to-all connectivity.

!!! warning "The initial state must be the ground state!"
    This transpiler stage assumes that the input state is $|0\rangle^{\otimes N}$, where $N$ is the number of qubits. The stage should not be used on sub-circuits where the input state is not $|0\rangle^{\otimes N}$.


This transpiler stage eliminates `Swap` gates by moving the gates preceding each `Swap` gate.

# Examples

```jldoctest
julia> transpiler = RemoveSwapBySwappingGatesTranspiler();

julia> circuit = QuantumCircuit(
                    qubit_count = 2,
                    instructions = [hadamard(1), swap(1, 2), sigma_x(2)]
                )
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H────☒───────
            |       
q[2]:───────☒────X──
                    



julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──────────
               
q[2]:──H────X──
               



```
