```
scatter(x,y)
scatter!(x,y)
```

`y` 対 `x` の散布図を作成します。

# キーワード引数

  * `markersize::Union{Real, AbstractVector}`: マーカーのサイズ（半径 ピクセル）。エイリアス: (:markersizes, :ms, :msize)。
  * `markercolor::Union{Integer, Symbol, ColorSchemes.ColorScheme, ColorTypes.Colorant}`: マーカーまたは形状の内部の色。 `:match` は `:seriescolor` の値を取ります。エイリアス: (:markercolors, :markercolour, :mc, :mcolor, :mcolour)。
  * `markershape::Union{Symbol, Plots.Shape, AbstractVector}`: [:none, :auto, :circle, :rect, :star5, :diamond, :hexagon, :cross, :xcross, :utriangle, :dtriangle, :rtriangle, :ltriangle, :pentagon, :heptagon, :octagon, :star4, :star6, :star7, :star8, :vline, :hline, :+, :x] から選択します。エイリアス: (:markershapes, :shape)。
  * `markeralpha::Real`: マーカー内部のアルファ/不透明度のオーバーライド。 `nothing`（デフォルト）は、markercolor のアルファ値を取ります。エイリアス: (:ma, :malpha, :markeralphas, :markeropacity, :mopacity, :mα)。

# 例

```julia-repl
julia> scatter([1,2,3],[4,5,6],markersize=[3,4,5],markercolor=[:red,:green,:blue])
julia> scatter([(1,4),(2,5),(3,6)])
```
