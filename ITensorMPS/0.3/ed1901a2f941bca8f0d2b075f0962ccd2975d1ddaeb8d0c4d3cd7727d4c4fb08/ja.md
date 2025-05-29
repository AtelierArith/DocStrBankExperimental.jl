```
removetags[!](linkinds, M::MPS, args...; kwargs...)
removetags[!](linkinds, M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのリンクインデックスにremovetagsを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。
