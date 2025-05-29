```
System(lat[, internal; T, μ, N, statistics])
```

与えられた格子とオプションの内部自由度を持つシステムを作成します。

## 引数

  * `lat`: システムの格子。
  * `internal`: 内部自由度の基底。

## キーワード引数

  * `T`: システムの温度。デフォルトは `0` です。
  * `μ`: システムの化学ポテンシャル。Unicode入力が利用できない場合は `mu` の同義語を使用してください。
  * `N`: システム内の粒子の数。
  * `statistics`: 粒子の統計。デフォルトは `FermiDirac` です。

## 例

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(3, 3);

julia> System(lat)
9サイトの2D空間における1粒子のSquareLattice

julia> System(lat, N=4, statistics=BoseEinstein)
9サイトの2D空間における4つの非相互作用ボース粒子のSquareLattice

julia> System(lat, mu=0, statistics=BoseEinstein)
9サイトの2D空間における固定されたμ=0.0の非相互作用ボース粒子のSquareLattice
```
