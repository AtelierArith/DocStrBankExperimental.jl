```
sticks(x,y)
sticks!(x,y)
```

Draw a stick plot of `y` vs `x`.

# Arguments

  * `fillrange::Union{Real, AbstractVector}`: Fills area between               fillrange and `y` for line-types, sets the base for               `bar`, `sticks` types, and similar for other types.               Aliases: (:fill_between, :fillbetween, :fillranges,               :fillrng, :fillto, :frange).
  * `markershape::Union{Symbol, Plots.Shape, AbstractVector}`:                 Choose from [:none, :auto, :circle, :rect, :star5,                 :diamond, :hexagon, :cross, :xcross, :utriangle,                 :dtriangle, :rtriangle, :ltriangle, :pentagon,                 :heptagon, :octagon, :star4, :star6, :star7, :star8,                 :vline, :hline, :+, :x]. Aliases: (:markershapes,                 :shape).

# Example

```julia-repl
julia> sticks(1:10)
```
