```
siteinds(uniqueinds, A::MPO, B::MPS, j::Integer; kwargs...)
siteinds(uniqueind, A::MPO, B::MPS, j::Integer; kwargs...)
```

MPO `A` に固有で、MPS/MPO `B` と共有されていないサイトインデックス（またはインデックス）を取得します。
