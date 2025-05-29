```
is_native_instruction(
    gate::Union{Gate},
    connectivity::Union{LineConnectivity,LatticeConnectivity},
    native_gates::Vector{DataType} = set_of_native_gates,
)::Bool
```

Returns `true` if the `gate` is a native instruction for the `connectivity` and the list of possible `native_gates`. The native gates for the Anyon QPUs are used by default.

A native instruction is defined as an instruction that is in `native_gates` and that satisifies the `connectivity`. It does not check to determine if the `gate` is placed at the `excluded_positions` or `excluded_connections` of the `connectivity`. The gate must operate on less than three qubits.

# Example

```jldoctest
julia> connectivity = LineConnectivity(3)
LineConnectivity{3}
1──2──3


julia> is_native_instruction(control_z(1, 2), connectivity)
true

julia> is_native_instruction(control_z(1, 3), connectivity)
false

julia> is_native_instruction(control_x(1, 2), connectivity)
false

julia> is_native_instruction(control_x(1, 2), connectivity, [Snowflurry.ControlX])
true

julia> is_native_instruction(toffoli(1, 2, 3), connectivity, [Snowflurry.Toffoli])
false

```
