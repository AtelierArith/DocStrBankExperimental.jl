```
draw!(fig, d::AbstractDrawable; axis=NamedTuple(), palettes=NamedTuple())
```

Draw a [`AlgebraOfGraphics.AbstractDrawable`](@ref) object `d` on `fig`. In practice, `d` will often be a [`AlgebraOfGraphics.Layer`](@ref) or [`AlgebraOfGraphics.Layers`](@ref). `fig` can be a figure, a position in a layout, or an axis if `d` has no facet specification. The output can be customized by giving axis attributes to `axis` or custom palettes to `palettes`.
