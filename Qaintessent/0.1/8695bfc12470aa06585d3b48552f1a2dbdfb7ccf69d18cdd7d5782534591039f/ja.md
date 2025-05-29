```
req_wires(cg::CircuitGate{M,G})
```

回路ゲート `cg` をホストするために回路に必要な最小限の量子ビットワイヤの数。

```jldoctest
julia> cg = circuit_gate(3, X, (1,2,5));
julia> req_wires(cg)
5
```
