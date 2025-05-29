```
replacetags[!](linkinds, M::MPS, args...; kwargs...)
replacetags[!](linkinds, M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのリンクインデックスにreplacetagsを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。
