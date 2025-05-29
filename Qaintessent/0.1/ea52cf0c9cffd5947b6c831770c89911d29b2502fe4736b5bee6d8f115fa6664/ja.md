```
ControlledGate{G}(U::G, M::Int) where {G<:AbstractGate}
```

はControlledGateオブジェクトを返します。`M`本の制御ワイヤーを持つタイプ`G`の[`AbstractGate`](@ref)を制御します。
