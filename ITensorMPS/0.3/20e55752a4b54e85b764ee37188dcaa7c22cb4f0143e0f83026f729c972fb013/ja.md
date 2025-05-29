```
setprime[!](linkinds, M::MPS, args...; kwargs...)
setprime[!](linkinds, M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのリンクインデックスにsetprimeを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。
