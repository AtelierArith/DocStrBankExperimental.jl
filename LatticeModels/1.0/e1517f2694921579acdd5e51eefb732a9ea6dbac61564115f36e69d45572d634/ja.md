```
NParticles(lat[, internal], N[; T=0, statistics=FermiDirac, occupations_type])
NParticles(sys, N[; T=0, statistics=FermiDirac, occupations_type])
```

与えられた格子と与えられた粒子数で多体システムを作成します。

## 引数

  * `lat`: システムの格子。
  * `internal`: 内部自由度の基底。
  * `sys`: 一粒子システム。
  * `N`: システム内の粒子数。

## キーワード引数

  * `T`: システムの温度。デフォルトは `0` です。
  * `statistics`: 粒子の統計。デフォルトは `FermiDirac` です。
  * `occupations_type`: 多体演算子の占有タイプ。デフォルトでは、占有数はベクトルに格納されますが、例えば、フェルミオンシステムのパフォーマンスを向上させるために `FermionBitstring` に設定することもできます。

## 例

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(3, 3);

julia> NParticles(lat, 4, statistics=BoseEinstein)
NParticles(4 bosons) on 9-site SquareLattice in 2D space
```
