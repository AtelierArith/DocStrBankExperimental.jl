```
move_instruction(
    original_readout::Readout,
    qubit_mapping::AbstractDict{T,T},
)::AbstractInstruction where {T<:Integer}
```

Returns a copy of `original_readout` where the qubits which the `original_readout` measures have been updated based on `qubit_mapping`.

The dictionary `qubit_mapping` contains key-value pairs describing how to update the target qubits. The key indicates which target qubit to change while the associated value specifies the new qubit.

# Examples

```jldoctest
julia> r = readout(1, 1)
Explicit Readout object:
   connected_qubit: 1 
   destination_bit: 1 

julia> move_instruction(r, Dict(1 => 2))
Explicit Readout object:
   connected_qubit: 2 
   destination_bit: 1 

```
