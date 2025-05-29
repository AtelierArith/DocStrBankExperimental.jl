```
dag[!](M::MPS, args...; kwargs...)
dag[!](M::MPO, args...; kwargs...)
```

MPS/MPOのすべてのITensorにdagを適用し、新しいMPS/MPOを返します。

MPS/MPOのITensorは、元のITensorのストレージのビューになります。あるいは、関数をインプレースで適用します。
