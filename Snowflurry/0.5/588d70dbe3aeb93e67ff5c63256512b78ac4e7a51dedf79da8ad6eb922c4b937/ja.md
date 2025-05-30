```
circuit_contains_gate_type(
    circuit::QuantumCircuit,
    gate_type::Type{<: AbstractGateSymbol}
)::Bool
```

回路に特定のゲートのタイプが存在するかどうかを判断します。

# 例

```jldoctest
julia> circuit = QuantumCircuit(qubit_count = 1, instructions = [sigma_x(1), sigma_y(1)])
Quantum Circuit Object:
   qubit_count: 1 
   bit_count: 1 
q[1]:──X────Y──
               
julia> circuit_contains_gate_type(circuit, Snowflurry.SigmaX)
true
               
julia> circuit_contains_gate_type(circuit, Snowflurry.ControlZ)
false
```
