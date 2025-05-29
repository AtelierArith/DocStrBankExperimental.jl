```
struct OwnAndGhostVectors{A,C,T}
```

ローカル値を格納するベクトルタイプ [`PVector`](@ref) インスタンスを、所有値のベクトル、ゴースト値のベクトル、および置換を使用して保存します。

# プロパティ

  * `own_values::A`: 所有値のベクトル。
  * `ghost_values::A`: ゴースト値のベクトル。
  * `permumation::C`: `vcat(own_values,ghost_values)[permutation]` がローカル値に対応するような置換ベクトル。

# スーパタイプ階層

```
OwnAndGhostVectors{A,C,T} <: AbstractVector{T}
```
