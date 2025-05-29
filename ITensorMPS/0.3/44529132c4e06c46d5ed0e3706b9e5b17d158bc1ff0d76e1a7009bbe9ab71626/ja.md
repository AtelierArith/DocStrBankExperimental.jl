```
removetags[!](M::MPS, args...; kwargs...)
removetags[!](M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのITensorにremovetagsを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。あるいは、関数をインプレースで適用します。
