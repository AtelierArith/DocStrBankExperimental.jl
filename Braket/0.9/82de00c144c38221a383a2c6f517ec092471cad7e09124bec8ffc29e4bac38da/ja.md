```
Braket.Probability(targets) -> Braket.Probability
Braket.Probability() -> Braket.Probability
```

`targets` に基づいて Braket.Probability を構築します。

`targets` は次のいずれかである可能性があります：

  * [`QubitSet`](@ref)
  * `Int` と/または [`Qubit`](@ref) の `Vector`
  * `Int` または `Qubit`
  * 不在の場合、測定はすべての量子ビットに適用されます。
