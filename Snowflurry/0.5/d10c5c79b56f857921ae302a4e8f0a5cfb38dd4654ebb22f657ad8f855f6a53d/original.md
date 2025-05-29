```
get_display_symbols(::Readout; precision::Integer = 4,)::Vector{String}
```

Returns a `Vector{String}` of the symbols that describe the `Readout`.

Each element in the `Vector` is associated with a qubit on which the `Readout` operates. This is useful for the placement of the `Readout` in a circuit diagram. The optional parameter `precision` has no effect for `Readout`.

# Examples

```jldoctest
julia> get_display_symbols(readout(2, 2))
1-element Vector{String}:
 "✲"

```
