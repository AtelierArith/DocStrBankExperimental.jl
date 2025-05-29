RejectGatesOnExcludedPositionsTranspiler

Transpiler stage which throws a `DomainError` if an `Instruction` in the `circuit` operates on an excluded qubit. The excluded qubits are specified with the parameter `excluded_positions` in certain `AbstractConnectivity` objects. The `circuit` remains unchanged if no error is thrown.

# Fields

  * connectivity::AbstractConnectivity – Connectivity where the `excluded_positions` are                                       specified.

# Examples

```jldoctest
julia> excluded_positions = [2];

julia> connectivity = LineConnectivity(4, excluded_positions)
LineConnectivity{4}
1──2──3──4
excluded positions: [2]


julia> transpiler = RejectGatesOnExcludedPositionsTranspiler(connectivity);

julia> invalid_circuit = QuantumCircuit(
               qubit_count = 4,
               instructions = [sigma_x(4), control_z(1, 2)],
           )
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:───────*──
            |  
q[2]:───────Z──
               
q[3]:──────────
               
q[4]:──X───────
               



julia> transpile(transpiler, invalid_circuit)
ERROR: DomainError with LineConnectivity{4}
1──2──3──4
excluded positions: [2]
:
the Gate{Snowflurry.ControlZ} on qubits [1, 2] cannot be applied since qubit 2 is unavailable
[...]

julia> valid_circuit = QuantumCircuit(
               qubit_count = 4,
               instructions = [sigma_x(1), control_z(3, 4)],
           )
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:──X───────
               
q[2]:──────────
               
q[3]:───────*──
            |  
q[4]:───────Z──
               



julia> transpiled_circuit = transpile(transpiler, valid_circuit)
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:──X───────
               
q[2]:──────────
               
q[3]:───────*──
            |  
q[4]:───────Z──
               



```
