```
Braket.Expectation(o, targets) -> Braket.Expectation
Braket.Expectation(o) -> Braket.Expectation
```

可観測量 `o` の Braket.Expectation をターゲットの量子ビット `targets` に対して構築します。

`o` は次のいずれかである可能性があります：

  * 任意の [`Observable`](@ref Braket.Observables.Observable)
  * `Observable` に対応する `String`（例：`"x"`）
  * 各要素が `Observable` に対応する `Vector{String}`

`targets` は次のいずれかである可能性があります：

  * [`QubitSet`](@ref)
  * `Int` と/または [`Qubit`](@ref) の `Vector`
  * `Int` または `Qubit`
  * 省略された場合、可観測量 `o` は単一の量子ビット可観測量である限り、すべての量子ビットに適用されます。
