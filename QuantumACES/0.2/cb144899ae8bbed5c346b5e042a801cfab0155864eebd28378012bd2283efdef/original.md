```
get_gate_data(total_gates::Vector{Gate}; combined::Bool = false, strict::Bool = false)
```

Returns the gate data for the gates `total_gates` in the form of a [`GateData`](@ref) object, combining Pauli X, Y, and Z basis SPAM noise if `combined` is `true`, and being strict about which gates count as estimable to additive or relative precision if `strict` is `true`.
