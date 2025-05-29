```
Braket.Variance(o, targets) -> Braket.Variance
Braket.Variance(o) -> Braket.Variance
```

観測量 `o` に対する Braket.Variance をターゲットの量子ビット `targets` に対して構築します。

`o` は次のいずれかである可能性があります：

  * 任意の [`Observable`](@ref Braket.Observables.Observable)
  * `Observable` に対応する `String`（例：`"x"`）
  * 各要素が `Observable` に対応する `Vector{String}`

`targets` は次のいずれかである可能性があります：

  * [`QubitSet`](@ref)
  * `Int` と/または [`Qubit`](@ref) の `Vector`
  * `Int` または `Qubit`
  * 不在の場合、観測量 `o` は単一の量子ビットの観測量である限り、すべての量子ビットに適用されます。
