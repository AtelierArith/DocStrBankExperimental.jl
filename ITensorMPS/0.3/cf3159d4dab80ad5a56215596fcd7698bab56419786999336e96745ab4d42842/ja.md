```
sim[!](siteinds, M::MPS, args...; kwargs...)
sim[!](siteinds, M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのサイトインデックスにsimを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。
