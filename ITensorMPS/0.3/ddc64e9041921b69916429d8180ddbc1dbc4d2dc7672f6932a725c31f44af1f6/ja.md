```
siteinds(commoninds, A::MPO, B::MPS, j::Integer; kwargs...)
siteinds(commonind, A::MPO, B::MPO, j::Integer; kwargs...)
```

`A`の`j`番目のMPOテンソルとMPS/MPO `B`で共有されているサイトインデックス（またはインデックス）を取得します。
