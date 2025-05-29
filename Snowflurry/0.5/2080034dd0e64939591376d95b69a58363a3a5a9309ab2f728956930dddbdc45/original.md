```
get_operator(gate::Gate)
```

Returns the `Operator` which is associated with a `Gate`.

# Examples

```jldoctest
julia> x = sigma_x(1);

julia> get_operator(get_gate_symbol(x))
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    1.0 + 0.0im    .


```
