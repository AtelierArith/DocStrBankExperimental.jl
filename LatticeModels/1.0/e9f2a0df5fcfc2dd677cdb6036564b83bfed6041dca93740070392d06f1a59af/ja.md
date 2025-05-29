```
Translation <: AbstractTranslation
```

ある格子上の空間的な変換。

## フィールド

  * `lat`: 変換が定義されている格子。
  * `R`: 変換のベクトル。

## 例

```jldoctest
julia> using LatticeModels

julia> gl = GenericLattice([(1, 1), (1, 2), (2, 1), (2, 2)])
4-site GenericLattice{GenericSite{2}} in 2D space:
  Site at [1.0, 1.0]
  Site at [1.0, 2.0]
  Site at [2.0, 1.0]
  Site at [2.0, 2.0]

julia> tr = Translation(gl, [1, 0])     # [1, 0]による変換
Translation by [1.0, 0.0]
 on 4-site GenericLattice{GenericSite{2}} in 2D space

julia> site1 = gl[!, x = 1, y = 1]      # [1, 1]のサイト
2-dim GenericSite{2} at [1.0, 1.0]

julia> site1 + tr                       # 変換されたサイト
2-dim GenericSite{2} at [2.0, 1.0]

julia> site1 - tr                       # 逆変換
2-dim GenericSite{2} at [0.0, 1.0]
```
