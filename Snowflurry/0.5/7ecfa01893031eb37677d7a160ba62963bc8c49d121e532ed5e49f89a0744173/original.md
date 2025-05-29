```
is_native_instruction(
    readout::Readout,
    connectivity::Union{LineConnectivity,LatticeConnectivity},
    native_gates::Vector{DataType} = set_of_native_gates,
)::Bool
```

Returns `true` if the `readout` satisfies the connectivity.

It does not check to determine if the `gate` is placed at the `excluded_positions` of the `connectivity`.

# Example

```jldoctest
julia> connectivity = LineConnectivity(3)
LineConnectivity{3}
1──2──3


julia> is_native_instruction(readout(2, 2), connectivity)
true

julia> is_native_instruction(readout(4, 4), connectivity)
false

```
