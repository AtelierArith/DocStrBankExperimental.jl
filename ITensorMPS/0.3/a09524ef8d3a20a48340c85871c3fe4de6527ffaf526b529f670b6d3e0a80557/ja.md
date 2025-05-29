```
setprime[!](siteinds, M::MPS, args...; kwargs...)
setprime[!](siteinds, M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのサイトインデックスにsetprimeを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。
