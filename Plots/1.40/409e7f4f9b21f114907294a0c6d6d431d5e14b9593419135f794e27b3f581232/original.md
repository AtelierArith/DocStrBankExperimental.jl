```
scatter(x,y)
scatter!(x,y)
```

Make a scatter plot of `y` vs `x`.

# Keyword arguments

  * `markersize::Union{Real, AbstractVector}`: Size (radius                pixels) of the markers. Aliases: (:markersizes, :ms,                :msize).
  * `markercolor::Union{Integer, Symbol,                 ColorSchemes.ColorScheme, ColorTypes.Colorant}`: Color of the                 interior of the marker or shape. `:match` will take                 the value from `:seriescolor`. Aliases:                 (:markercolors, :markercolour, :mc, :mcolor, :mcolour).
  * `markershape::Union{Symbol, Plots.Shape, AbstractVector}`:                 Choose from [:none, :auto, :circle, :rect, :star5,                 :diamond, :hexagon, :cross, :xcross, :utriangle,                 :dtriangle, :rtriangle, :ltriangle, :pentagon,                 :heptagon, :octagon, :star4, :star6, :star7, :star8,                 :vline, :hline, :+, :x]. Aliases: (:markershapes,                 :shape).
  * `markeralpha::Real`: The alpha/opacity override for the                 marker interior. `nothing` (the default) means it                 will take the alpha value of markercolor.                 Aliases: (:ma, :malpha, :markeralphas,                 :markeropacity, :mopacity, :mα).

# Examples

```julia-repl
julia> scatter([1,2,3],[4,5,6],markersize=[3,4,5],markercolor=[:red,:green,:blue])
julia> scatter([(1,4),(2,5),(3,6)])
```
