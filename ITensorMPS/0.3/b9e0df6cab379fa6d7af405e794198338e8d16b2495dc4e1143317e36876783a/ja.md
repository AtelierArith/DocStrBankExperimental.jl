```
settags[!](M::MPS, args...; kwargs...)
settags[!](M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのITensorにsettagsを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。あるいは、関数をインプレースで適用します。
