```
tidyup!(A::QuantumObject, tol::Real=settings.tidyup_tol)
```

与えられた [`QuantumObject`](@ref) `A` に対して、各要素の実部と虚部をそれぞれチェックします。絶対値が `tol` より小さい実部または虚部の値を削除します。

この関数は [`tidyup`](@ref) のインプレースバージョンであることに注意してください。
