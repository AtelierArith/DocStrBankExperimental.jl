```
removetags[!](siteinds, M::MPS, args...; kwargs...)
removetags[!](siteinds, M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのサイトインデックスにremovetagsを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。
