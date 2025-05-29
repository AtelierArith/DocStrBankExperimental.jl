```
get_circuit_instructions(circuit::QuantumCircuit)::Vector{AbstractInstruction}
```

Returns the list of instructions in the `circuit`.

# Examples

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2, instructions = [hadamard(1), control_z(1, 2)]);

julia> get_circuit_instructions(c)
2-element Vector{AbstractInstruction}:
 Gate Object: Snowflurry.Hadamard
Connected_qubits	: [1]
Operator:
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.7071067811865475 + 0.0im    0.7071067811865475 + 0.0im
0.7071067811865475 + 0.0im    -0.7071067811865475 + 0.0im

 Gate Object: Snowflurry.ControlZ
Connected_qubits	: [1, 2]
Operator:
(4, 4)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    -1.0 + 0.0im


```
