```
setprime[!](M::MPS, args...; kwargs...)
setprime[!](M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのITensorにsetprimeを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。あるいは、関数をインプレースで適用します。
