```
replacetags[!](siteinds, M::MPS, args...; kwargs...)
replacetags[!](siteinds, M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのサイトインデックスにreplacetagsを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。
