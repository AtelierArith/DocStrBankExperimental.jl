```
circuit_gate
```

基本ゲートタイプから[`CircuitGate`](@ref)オブジェクトを構築するためのヘルパー関数。

```jldoctest
julia> circuit_gate(1, X)
CircuitGate{1,XGate}((1,), XGate())

julia> circuit_gate(1, X, 2)
CircuitGate{2,ControlledGate{XGate}}((1, 2), ControlledGate{XGate}(XGate(), 1))

julia> circuit_gate((1,2), SwapGate(), (3,4))
CircuitGate{4,ControlledGate{SwapGate}}((1, 2, 3, 4), ControlledGate{SwapGate}(SwapGate(), 2))
```
