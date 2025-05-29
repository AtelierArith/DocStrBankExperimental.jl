```
settags[!](linkinds, M::MPS, args...; kwargs...)
settags[!](linkinds, M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのリンクインデックスにsettagsを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。
