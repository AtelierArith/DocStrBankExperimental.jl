```
sim[!](siteinds, uniqueinds, M1::MPO, M2::MPS, args...; kwargs...)
```

`M1`と共有されていないサイトインデックスの`M2`に対してsimを適用します。新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。
