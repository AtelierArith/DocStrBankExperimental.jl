```
addtags[!](M::MPS, args...; kwargs...)
addtags[!](M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのITensorにaddtagsを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。あるいは、関数をインプレースで適用します。
