```
sticks(x,y)
sticks!(x,y)
```

`y` と `x` のスティックプロットを描画します。

# 引数

  * `fillrange::Union{Real, AbstractVector}`: 線の種類のために `fillrange` と `y` の間の領域を塗りつぶし、`bar`、`sticks` タイプの基準を設定し、他のタイプにも同様に適用します。エイリアス: (:fill_between, :fillbetween, :fillranges, :fillrng, :fillto, :frange)。
  * `markershape::Union{Symbol, Plots.Shape, AbstractVector}`: [:none, :auto, :circle, :rect, :star5, :diamond, :hexagon, :cross, :xcross, :utriangle, :dtriangle, :rtriangle, :ltriangle, :pentagon, :heptagon, :octagon, :star4, :star6, :star7, :star8, :vline, :hline, :+, :x] から選択します。エイリアス: (:markershapes, :shape)。

# 例

```julia-repl
julia> sticks(1:10)
```
