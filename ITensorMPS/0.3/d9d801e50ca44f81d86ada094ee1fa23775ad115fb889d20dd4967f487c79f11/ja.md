```
prime[!](M::MPS, args...; kwargs...)
prime[!](M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのITensorにprimeを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。あるいは、関数をインプレースで適用します。
