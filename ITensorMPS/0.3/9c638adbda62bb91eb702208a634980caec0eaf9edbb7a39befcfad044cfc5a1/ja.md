```
prime[!](siteinds, uniqueinds, M1::MPO, M2::MPS, args...; kwargs...)
```

`M2`と共有されていない`M1`のサイトインデックスにprimeを適用します。新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。
