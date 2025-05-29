```
CircuitGate{M,G}(iwire::NTuple{M,<:Integer}, gate::G) where {M,G}
```

`CircuitGate{M,G}`オブジェクトを作成します。`M`はCircuitGateに影響を与えるワイヤの数であり、`G`はCircuitGateを構築するために使用される基本ゲートです。
