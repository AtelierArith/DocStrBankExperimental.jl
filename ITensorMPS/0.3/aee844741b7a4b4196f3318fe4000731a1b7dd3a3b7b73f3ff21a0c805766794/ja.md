```
swapprime[!](M::MPS, args...; kwargs...)
swapprime[!](M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのITensorにswapprimeを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。あるいは、関数をインプレースで適用します。
