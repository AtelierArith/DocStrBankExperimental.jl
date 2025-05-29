```
replacetags[!](M::MPS, args...; kwargs...)
replacetags[!](M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのITensorにreplacetagsを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。あるいは、関数をインプレースで適用します。
