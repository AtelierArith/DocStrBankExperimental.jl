```
siteinds(uniqueinds, A::MPO, B::MPS)
siteinds(uniqueind, A::MPO, B::MPO)
```

MPO `A` に固有で、MPS/MPO `B` と共有されていないサイトインデックスを取得し、`Vector{<:Index}` として返します。
