```
calc_bz(real_latvecs,atom_types,atom_pos,coordinates,bzformat,makeprim,
    convention,library;rtol,atol)
```

与えられた実空間格子基底のためのブリルアンゾーンを計算します。

# 引数

  * `real_latvecs::AbstractMatrix{<:Real}`: 実空間格子ベクトルまたは 2x2 または 3x3 行列の列としての原始的な翻訳ベクトル。
  * `atom_typesAbstractVector{<:Int}`: 整数としての原子タイプのリスト。
  * `atom_pos::AbstractMatrix{<:Real}`: 結晶構造内の原子の位置を行列の列として表したもの。
  * `coordinates::String`: 原子の位置が「格子」または「デカルト」座標であることを示します。
  * `bzformat::String`: ブリルアンゾーンの形式。オプションには「凸包」と「半空間」が含まれます。
  * `makeprim::Bool=false`: `true` の場合、BZを計算する前に単位セルを原始的にします。
  * `convention::String="ordinary"`: 実空間と逆空間の間を移動するために使用される規約。2つの規約は、通常（時間的）周波数と角周波数です。実空間から逆空間への変換は、規約が通常であればユニタリです。
  * `library::Polyhedra.Library=CDDLib.Library()`: 多面体操作ライブラリ
  * `rtol::Real=sqrt(eps(float(maximum(real_latvecs))))` 浮動小数点比較のための相対許容誤差。
  * `atol::Real=1e-9`: 浮動小数点比較のための絶対許容誤差。

# 戻り値

  * `bz`: ブリルアンゾーンの凸包を表す Polyhedra.jl インターフェースに準拠した多面体。

# 例

```jldoctest
using SymmetryReduceBZ
real_latvecs = [1 0; 0 1]
convention="ordinary"
atom_types=[0]
atom_pos = Array([0 0]')
coordinates = "Cartesian"
makeprim=false
SymmetryReduceBZ.Symmetry.calc_bz(real_latvecs,atom_types,atom_pos,coordinates,
    makeprim,convention)
# 出力
Polyhedron CDDLib.Polyhedron{Float64}:
25-element iterator of Polyhedra.HalfSpace{Float64, Vector{Float64}}:
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
4-element iterator of Vector{Float64}:
 [0.5, 0.5]
 [0.5, -0.5]
 [-0.5, -0.5]
 [-0.5, 0.5]
```
