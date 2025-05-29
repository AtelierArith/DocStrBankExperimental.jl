```
get_gate_symbol(gate::Gate)::AbstractGateSymbol
```

Returns the symbol that is associated with a `gate`.

# Examples

```jldoctest
julia> gate = sigma_x(1);

julia> get_gate_symbol(gate)
Snowflurry.SigmaX()

```
