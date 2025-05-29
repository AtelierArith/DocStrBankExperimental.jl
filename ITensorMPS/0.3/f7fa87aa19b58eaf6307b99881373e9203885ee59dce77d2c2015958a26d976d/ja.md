```
addtags[!](linkinds, M::MPS, args...; kwargs...)
addtags[!](linkinds, M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのリンクインデックスにaddtagsを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。
