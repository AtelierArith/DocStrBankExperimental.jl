```
create_gate_1q(gate_label::String, mat::Array{Complex{Float64},2})
```

Creates a new user-defined gate, caches the generating matrix, and returns the GateOps.GateSymbol key for use in a circuit. Matrix is converted to 2x2 StaticArrays SMatrix internally.

# Examples

```julia-repl

```
