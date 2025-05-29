```julia
ptranspose(ρ, idims, isystems)

```

  * `ρ`: 量子状態。
  * `idims`: サブシステムの次元。
  * `isystems`: 転置されたサブシステム。

行列 `ρ` の [部分転置](http://en.wikipedia.org/wiki/Peres-Horodecki_criterion) を、`isystems` によって決定されたサブシステムに対して返します。
