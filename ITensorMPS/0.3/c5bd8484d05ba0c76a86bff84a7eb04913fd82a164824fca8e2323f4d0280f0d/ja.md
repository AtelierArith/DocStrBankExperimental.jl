```
replaceprime[!](M::MPS, args...; kwargs...)
replaceprime[!](M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのITensorにreplaceprimeを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。あるいは、関数をインプレースで適用します。
