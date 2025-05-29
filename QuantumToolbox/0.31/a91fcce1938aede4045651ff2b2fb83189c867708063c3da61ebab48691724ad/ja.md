```
const PhysicalConstants
```

`NamedTuple` は、[ *CODATA 推奨値の基本物理定数: 2022* ](https://physics.nist.gov/cuu/pdf/wall_2022.pdf) にリストされたいくつかの定数値を格納します。

現在格納されている定数は次のとおりです：

  * `c` : (正確) 真空中の光の速度、単位 $[\textrm{m}\cdot\textrm{s}^{-1}]$
  * `G` : ニュートン重力定数、単位 $[\textrm{m}^3\cdot\textrm{kg}^{−1}\cdot\textrm{s}^{−2}]$
  * `h` : (正確) プランク定数、単位 $[\textrm{J}\cdot\textrm{s}]$
  * `ħ` : 縮小プランク定数、単位 $[\textrm{J}\cdot\textrm{s}]$
  * `e` : (正確) 基本電荷、単位 $[\textrm{C}]$
  * `μ0` : 真空中の磁気透過率、単位 $[\textrm{N}\cdot\textrm{A}^{-2}]$
  * `ϵ0` : 真空中の電気的誘電率、単位 $[\textrm{F}\cdot\textrm{m}^{-1}]$
  * `k` : (正確) ボルツマン定数、単位 $[\textrm{J}\cdot\textrm{K}^{-1}]$
  * `NA` : (正確) アボガドロ定数、単位 $[\textrm{mol}^{-1}]$

# 例

```jldoctest
julia> PhysicalConstants.ħ
1.0545718176461565e-34
```
