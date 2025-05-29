```
plot_convexhulls(real_latvecs,atom_types,atom_pos,coords,makeprim,convention;rtol,atol)
```

2Dまたは3Dでブリルアンゾーンと不可約ブリルアンゾーンをプロットします。

!!! note "Julia 1.9以降"
    この関数はパッケージ拡張に実装されており、`using PyPlot`が必要です。


# 引数

  * `real_latvecs::AbstractMatrix{<:Real}`: 行列の列としての実空間格子の基底。
  * `atom_types:AbstractVector{<:Int}`: 整数としての原子タイプのリスト。
  * `atom_pos::AbstractMatrix{<:Real}`: 行列の列としての結晶構造内の原子の位置。
  * `coords::String`: 原子の位置が「格子」または「デカルト」座標であることを示します。
  * `makeprim::Bool=false`: `true`の場合、IBZを計算する前に単位セルを原始的にします。
  * `convention::String="ordinary"`: 実空間と逆空間の間を移動するために使用される規約。2つの規約は通常（時間的）周波数と角周波数です。実空間から逆空間への変換は、規約が通常であればユニタリです。
  * `library::Polyhedra.Library=CDDLib.Library()`: 多面体操作ライブラリ
  * `rtol::Real=sqrt(eps(float(maximum(real_latvecs))))` 浮動小数点比較のための相対許容誤差。
  * `atol::Real=1e-9`: 浮動小数点比較のための絶対許容誤差。

# 戻り値

  * `ax::PyObject`: BZとIBZのプロットで更新された`ax`。

# 例

```julia
ENV["MPLBACKEND"]="qt5agg"
using PyPlot
using SymmetryReduceBZ
real_latvecs = [1 0; .5 1]
atom_types=[0]
atom_pos = Array([0 0]')
coords = "Cartesian"
makeprim = true
convention = "ordinary"
ax=plot_convexhulls(real_latvecs,atom_types,atom_pos,coords,makeprim,convention)
# output
PyObject <AxesSubplot: >
```
