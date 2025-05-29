```
prime[!](siteinds, M::MPS, args...; kwargs...)
prime[!](siteinds, M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのサイトインデックスにprimeを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。
