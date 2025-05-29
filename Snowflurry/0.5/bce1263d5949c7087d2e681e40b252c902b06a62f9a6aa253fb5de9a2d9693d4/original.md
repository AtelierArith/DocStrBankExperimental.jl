```
get_display_symbols(gate::AbstractGateSymbol; precision::Integer = 4,)::Vector{String}
```

Returns a `Vector{String}` of the symbols that describe the `gate`.

Each element in the `Vector` is associated with a qubit on which the `gate` operates. This is useful for the placement of the `gate` in a circuit diagram. The optional parameter `precision` enables setting the number of digits to keep after the decimal for `gate` parameters.

# Examples

```jldoctest
julia> get_display_symbols(get_gate_symbol(control_z(1, 2)))
2-element Vector{String}:
 "*"
 "Z"

julia> get_display_symbols(get_gate_symbol(phase_shift(1, π/2)), precision = 3)
1-element Vector{String}:
 "P(1.571)"

```
