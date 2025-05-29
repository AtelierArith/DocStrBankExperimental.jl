```julia
ptrace(ρ, idims, isystems)

```

  * `ρ`: 量子状態。
  * `idims`: サブシステムの次元。
  * `isystems`: トレースされたサブシステム。

`isystems`によって決定されたサブシステムに対する行列`ρ`の[部分トレース](https://en.wikipedia.org/wiki/Partial_trace)を返します。
