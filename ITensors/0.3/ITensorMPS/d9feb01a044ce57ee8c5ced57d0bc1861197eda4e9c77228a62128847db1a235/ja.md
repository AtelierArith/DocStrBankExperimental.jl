```
siteinds(uniqueinds, A::MPO, B::MPS)
siteinds(uniqueind, A::MPO, B::MPO)
```

MPO `A` のサイトインデックスを取得します。これは `B` の MPS/MPO と共有されていない `A` に固有のもので、`Vector{<:Index}` として返されます。
