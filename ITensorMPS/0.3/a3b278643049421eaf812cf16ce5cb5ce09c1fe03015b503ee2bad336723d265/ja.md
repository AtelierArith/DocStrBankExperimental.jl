```
prime[!](siteinds, commoninds, M1::MPO, M2::MPS, args...; kwargs...)
prime[!](siteinds, commoninds, M1::MPO, M2::MPO, args...; kwargs...)
```

`M1`と`M2`で共有されるサイトインデックスに対してprimeを適用します。

新しいMPS/MPOを返します。MPS/MPOのITensorは、元のITensorのストレージのビューになります。
