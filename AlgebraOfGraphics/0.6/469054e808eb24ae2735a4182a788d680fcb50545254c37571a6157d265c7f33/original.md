```
draw(d; axis=NamedTuple(), figure=NamedTuple, palettes=NamedTuple())
```

Draw a [`AlgebraOfGraphics.AbstractDrawable`](@ref) object `d`. In practice, `d` will often be a [`AlgebraOfGraphics.Layer`](@ref) or [`AlgebraOfGraphics.Layers`](@ref). The output can be customized by giving axis attributes to `axis`, figure attributes to `figure`, or custom palettes to `palettes`. Legend and colorbar are drawn automatically. For finer control, use [`draw!`](@ref), [`legend!`](@ref), and [`colorbar!`](@ref) independently.
