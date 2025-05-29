```
move_instruction(gate::Gate,
    qubit_mapping::AbstractDict{<:Integer,<:Integer})::AbstractGateSymbol
```

Returns a copy of `gate` where the qubits on which the `gate` acts have been updated based on `qubit_mapping`.

The dictionary `qubit_mapping` contains key-value pairs describing how to update the target qubits. The key indicates which target qubit to change while the associated value specifies the new qubit.

# Examples

```jldoctest
julia> gate = sigma_x(1)
Gate Object: Snowflurry.SigmaX
Connected_qubits	: [1]
Operator:
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    1.0 + 0.0im    .


julia> move_instruction(gate, Dict(1=>2))
Gate Object: Snowflurry.SigmaX
Connected_qubits	: [2]
Operator:
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    1.0 + 0.0im    .


```
