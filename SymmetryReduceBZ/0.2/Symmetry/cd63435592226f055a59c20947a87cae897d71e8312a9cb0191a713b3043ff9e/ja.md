```
calc_ibz(real_latvecs,atom_types,atom_pos,coordinates,ibzformat,makeprim,
    convention,library;rtol,atol)
```

2Dまたは3Dの結晶構造の不可約ブリルアンゾーンを計算します。

# 引数

  * `real_latvecs::AbstractMatrix{<:Real}`: 行列の列としての実空間格子の基底。
  * `atom_types:AbstractVector{<:Int}`: 整数としての原子タイプのリスト。
  * `atom_pos::AbstractMatrix{<:Real}`: 行列の列としての結晶構造内の原子の位置。
  * `coordinates::String`: 原子の位置が「格子」または「デカルト」座標であることを示します。
  * `ibzformat::String`: 不可約ブリルアンゾーンの形式。オプションには「凸包」と「半空間」が含まれます。
  * `makeprim::Bool=false`: trueの場合、IBZを計算する前に単位セルを原始的にします。
  * `convention::String="ordinary"`: 実空間と逆空間の間を移動するために使用される規約。2つの規約は、通常（時間的）周波数と角周波数です。実空間から逆空間への変換は、規約が通常であればユニタリです。
  * `library::Polyhedra.Library=CDDLib.Library()`: 多面体操作ライブラリ
  * `rtol::Real=sqrt(eps(float(maximum(real_latvecs))))` 浮動小数点比較のための相対許容誤差。
  * `atol::Real=1e-9`: 浮動小数点比較のための絶対許容誤差。

# 戻り値

  * `ibz`: Polyhedra.jlインターフェースに準拠した多面体としての不可約ブリルアンゾーン。

# 例

```jldoctest
using SymmetryReduceBZ
real_latvecs = [1 0; 0 1]
convention="ordinary"
atom_types=[0]
atom_pos = Array([0 0]')
coordinates = "Cartesian"
makeprim=false
SymmetryReduceBZ.Symmetry.calc_ibz(real_latvecs,atom_types,atom_pos,coordinates,
    makeprim,convention)
# output
Polyhedron CDDLib.Polyhedron{Float64}:
32-element iterator of Polyhedra.HalfSpace{Float64, Vector{Float64}}:
 HalfSpace([-2.0, -2.0], 4.0)
 HalfSpace([-2.0, -1.0], 2.5)
 HalfSpace([-2.0, 0.0], 2.0)
 HalfSpace([-2.0, 1.0], 2.5)
 HalfSpace([-2.0, 2.0], 4.0)
 HalfSpace([-1.0, -2.0], 2.5)
 HalfSpace([-1.0, -1.0], 1.0)
 HalfSpace([-1.0, 0.0], 0.5)
 HalfSpace([-1.0, 1.0], 1.0)
 HalfSpace([-1.0, 2.0], 2.5)
 HalfSpace([0.0, -2.0], 2.0)
 HalfSpace([0.0, -1.0], 0.5)
 HalfSpace([0.0, 0.0], 0.0)
 HalfSpace([0.0, 1.0], 0.5)
 HalfSpace([0.0, 2.0], 2.0)
 HalfSpace([1.0, -2.0], 2.5)
 HalfSpace([1.0, -1.0], 1.0)
 HalfSpace([1.0, 0.0], 0.5)
 HalfSpace([1.0, 1.0], 1.0)
 HalfSpace([1.0, 2.0], 2.5)
  ⋮:
3-element iterator of Vector{Float64}:
 [0.0, 0.0]
 [0.5, 0.0]
 [0.5, 0.5]
```
