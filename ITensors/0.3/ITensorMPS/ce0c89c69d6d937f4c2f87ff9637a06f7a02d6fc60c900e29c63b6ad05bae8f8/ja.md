```
siteinds(commoninds, A::MPO, B::MPS; kwargs...)
siteinds(commonind, A::MPO, B::MPO; kwargs...)
```

MPO `A` と MPS/MPO `B` で共有されているサイトインデックス（またはインデックス）のベクトルを取得します。
